pipeline {
   agent any
environment { 
   NAME = "ticketbooking"
   VERSION = "${env.BUILD_ID}-${env.GIT_COMMIT}"
   IMAGE = "${NAME}:${VERSION}"
   IMAGE_REPO="durgagupta"
   IMAGE_URL='hub.docker.com'
   }
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
  
stage('Docker Build result') {
     steps {
            echo "Running ${VERSION} on ${env.JENKINS_URL}"
            sh "docker build -t ${NAME} ."
            sh "docker tag ${NAME}:latest ${IMAGE_REPO}/${NAME}:${VERSION}"
        }
    }
     stage('Push result image') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockeruser', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh "docker push ${IMAGE_REPO}/${NAME}:${VERSION}"
           
        }
      }
    }
  }
  }

