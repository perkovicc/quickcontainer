pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = "myapp"
        CONTAINER_NAME = "mydemo"
        DOMAIN = "perrky.icu"
        SUBDOMAIN = "mydemo"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Images') {
            steps {
                script {
                    sh 'docker-compose build'
                }
            }
        }

        stage('Run Containers') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Example: run tests inside container
                    sh 'docker-compose exec web pytest tests/'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    sh 'docker-compose down'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete. Cleaning up...'
            sh 'docker-compose down -v'
        }
    }
}