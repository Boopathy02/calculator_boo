pipeline {
    agent any 
    tools {
        node "nodejs"
    }
    environment {
        docker_image_name = 'nodejs_calculater'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'git@github.com:vanthiyadhevan/nodejs_calculater.git', branch: 'main', credentialsId: 'vanthiyadhevan'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'ng test'
            }
        }
        stage('Test E2E') {
            steps {
                sh 'ng e2e'
            }
        }
        stage('Build As Docker Image') {
            steps {
                script {
                    docker.build("${docker_image_name}:${BUILD_NUMBER}", "Dockerfile")
                }
            }
        }
    }
}
