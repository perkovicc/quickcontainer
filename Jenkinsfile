pipeline {
    agent { label 'netcup-vps' }

    stages {
        stage('Compose Up') {
            steps {
                sh 'docker compose up -d'
            }
        }
    }
}