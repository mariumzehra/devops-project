pipeline {
    agent any
    environment {
        PATH = "C:\\Users\\HP Probook\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin;${env.PATH}"
    }
    stages {
        stage('Clone') {
            steps { git branch: 'main', url: 'https://github.com/mariumzehra/devops-project.git' }
        }
        stage('Build Images') {
            steps { bat 'docker-compose build' }
        }
         stage('Run Containers') {
            steps {
                bat 'docker rm -f web-app nginx-proxy mysql-db || exit 0'
                bat 'docker-compose down'
                bat 'docker-compose up -d'
            }
        }
        stage('Verify') {
            steps { bat 'docker ps' }
        }
    }
}