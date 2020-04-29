pipeline {
  
  environment {
    registry = "docker_hub_account/repository_name"
    registryCredential = 'dockerhub'
  }
  agent any
  

  stages {  // Define the individual processes, or stages, of your CI pipeline
    
    stage('Checkout') { // Checkout (git clone ...) the projects repository //test git-push
      
      steps {
        checkout scm
        
      }
    }
    
    stage('Building image') {
      steps{
        script {
          docker.build("image_api","./simple_api/")
       }
      }
    }
    
    stage ('Test image') {
      agent{
        docker {image'image_api'}
      }
      steps {
      sh 'python /student_age.py'}
    }
    
    
}
}
