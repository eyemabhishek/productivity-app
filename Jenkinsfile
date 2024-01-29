pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Client Tests') {
      steps {
        dir(path: 'client') {
          sh 'npm install'
          sh 'npm test'
        }

      }
    }

    stage('Build Client Image'){
        steps{
            sh 'docker build -t prosoftdevops/productivity-app:client-latest client'   
        }
        
    }

    stage('Push Image to Docker Hub'){
        steps{
            withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
			sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
			sh 'docker push prosoftdevops/productivity-app:client-latest'
		}
        }
    }






  }
   
}