pipeline{
agent any

  tools {
   maven 'Maven3'
  }

   stages{
   stage('GIT'){
      steps{
         git branch: 'Feature-1', credentialsId: 'GitHub', url: 'https://github.com/lakshmisagarhe/maven-project.git'
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
