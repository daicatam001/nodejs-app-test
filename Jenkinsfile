pipeline {
  agent any

  environment {
    APP_NAME = "node-app"
  }

  stages {

    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/daicatam001/nodejs-app-test.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker compose build'
        sh 'ls -la'
      }
    }
    

    stage('Stop Old Containers') {
      steps {
        echo 'Stopping old containers...'
        sh 'docker compose down'
      }
    }

    stage('Start New Containers') {
      steps {
        echo 'Starting new containers...'
        sh 'docker compose up -d'
      }
    }

  }

  post {
    success {
      echo 'Deployment successful!'
    }
    failure {
      echo 'Deployment failed!'
    }
  }
}