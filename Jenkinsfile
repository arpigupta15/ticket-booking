pipeline {
   agent any

  stages {
    stage('Cloning Git') {
      steps {
       git branch: 'main', url:'https://github.com/arpigupta15/ticket-booking.git'
      }
    }
     stage('Compile Package and Create war file') {
      steps {
        sh "mvn package"
      }
    }
  }
  }