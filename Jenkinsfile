pipeline {
    agent any
    stages {
        stage('Clone') {
            steps { git branch: 'main', url: 'https://github.com/USERNAME/REPO.git' }
        }
        stage('Build Images') {
            steps { bat 'docker compose build' }
        }
        stage('Run Containers') {
            steps {
                bat 'docker compose down'
                bat 'docker compose up -d'
            }
        }
        stage('Verify') {
            steps { bat 'docker ps' }
        }
    }
}