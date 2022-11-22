pipeline{
agent any

  tools {
   maven 'Maven3'
  }

   stages{
   stage('GIT'){
      steps{
         git branch: 'main', url: 'https://github.com/lakshmisagarhe/assignment.git'
      }
   }

   stage('Maven'){
      steps{
         sh 'mvn clean install -f pom.xml'
      }
   }

   stage('Tomcat'){
      steps{
         deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://43.205.194.83:8080/')], contextPath: '/pipeline', war: '**/*.war'
       }
   }
   }
}
