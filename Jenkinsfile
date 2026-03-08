pipeline {
  agent any

  stages {

    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Compile') {
      steps {
        sh 'javac Hello.java'
      }
    }

    stage('Run') {
      steps {
        sh 'java Hello'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t abdullah1234567/hello-ci:latest .'
      }
    }

    stage('Push Docker Image') {
      steps {
        sh 'docker push abdullah1234567/hello-ci:latest'
      }
    }
    stage('Deploy Container') {
  steps {
    sh 'docker rm -f hello-container || true'
    sh 'docker run --name hello-container abdullah1234567/hello-ci:latest'
  }
}

  }
}
