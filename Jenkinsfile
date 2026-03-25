pipeline {
    agent any

    environment {
        IMAGE_NAME = 'jenkins-ci-cd-app'
        CONTAINER_NAME = 'jenkins-ci-cd-container'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'git@github.com:abdullahalhussein25-dot/jenkins-ci-cd-.git'
            }
        }

        stage('Build Maven') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                    docker stop $CONTAINER_NAME || true
                    docker rm $CONTAINER_NAME || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name $CONTAINER_NAME -p 8081:8081 $IMAGE_NAME'
            }
        }
    }
}
