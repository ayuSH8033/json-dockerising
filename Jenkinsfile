pipeline{
    agent any
    options{
        buildDiscarder(logRotator(numToKeepStr: '5', daysToKeepStr: '5'))
        timestamps()
    }
    environment{
        
        registry = "ayushthakur123/json-project"
        registryCredential = 'new-token'        
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
            docker.withRegistry( '', 94fbb51c-222c-4bdd-9c69-94c9b90d817c ) {
            dockerImage.push()
          }
        }
      }
    }
}
