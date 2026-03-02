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
  }
}
