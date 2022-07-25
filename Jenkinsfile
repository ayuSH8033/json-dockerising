pipeline{
    agent any
    options{
        buildDiscarder(logRotator(numToKeepStr: '5', daysToKeepStr: '5'))
        timestamps()
    }
    environment{
        
        registry = "ayushthakur123/json-project"
        registryCredential = 'ayushthakur123'        
    }
    
    stages{
       stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
       stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', 415f56aa-fbf1-4857-83f1-508821825e56 ) {
            dockerImage.push()
          }
        }
      }
    }
}
