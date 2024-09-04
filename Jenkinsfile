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
       stage('Deploy to Tomcat') {
      steps {
        
         sh "cp /var/lib/jenkins/workspace/Ticketbooking/target/TrainBook-1.0.0-SNAPSHOT.war /opt/tomcat/webapps/"
      }
    }
  }
  }

