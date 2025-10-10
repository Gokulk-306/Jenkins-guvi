// 1. Clone source code from github 
// 2. build docker image from code
// 3. Login to Dockerhub
// 4. Push the image to dockerhub

pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
        IMAGE_NAME = "gokulk306/jenkins_demo"
    }
    stages {
        stage('Clone repo') {
            steps {
                git branch: 'main', url: ''
            }
        }

        stage('Build Docker image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME:latest .'
                }
            }
        }

         stage('Login to dockerhub') {
            steps {
                script {
                    sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                }
            }
        }

        stage('Push image to dockerhub') {
            steps {
                script {
                    sh 'docker push $IMAGE_NAME:latest'
                }
            }
        }
    }
}