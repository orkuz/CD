pipeline {
    agent any
    
    stages {
        stage('Run docker compose') {
            steps {
                echo 'Starting docker containers...'
                dir('docker'){
                    sh 'docker compose up -d'
                }
            }
        }
    }
}