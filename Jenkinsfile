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

    stage('Build Client Image')
    steps{
        sh 'docker build -t prosoftdevops/productivity-app:client-latest client'
    }

  }
}