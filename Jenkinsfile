pipeline {
  
  environment {
    registry = "306655/image_api_repo"
    registryCredential = 'dockerhub'
  }
  agent any
  

  stages {  // Define the individual processes, or stages, of your CI pipeline
    
    stage('Checkout') { // Checkout (git clone ...) the projects repository //test git-push
      
      steps {
        checkout scm
        
      }
    }
    
    stage('Building image') { //building image
      steps{
        script {
          docker.build("306655/image_api_repo","./simple_api/")
       }
      }
    }
    
    stage ('Test image') { // test image 
      agent{
        docker {image'306655/image_api_repo'}
      }
      steps {
      sh "curl -u toto:python -X GET http://localhot:5000/pozos/api/v1.0/get_student_ages"}
    }
    
    stage ( 'push image' ) { //push image
      steps {
        script {
        docker.withRegistry('https://hub.docker.com/r/306655/image_api_repo','registryCredential') {
          dockerImage.push() }
        }
      }
    }
    
}
}
