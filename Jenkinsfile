pipeline {
  
  environment {
    registry = "docker_hub_account/repository_name"
    registryCredential = 'dockerhub'
  }
  agent any
  

  stages {  // Define the individual processes, or stages, of your CI pipeline
    
    
    stage('Building image') {
      steps{
        script {
          docker.build("image_api","./simple_api/")
       }
      }
    }
    
    
    stage('Checkout') { // Checkout (git clone ...) the projects repository //test git-push
      
      steps {
        checkout scm
        
      }
    }
    
}
}
