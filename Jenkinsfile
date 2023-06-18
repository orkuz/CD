pipeline {
    agent any
    
    stages {
        stage('Run docker compose') {
            steps {
                echo 'Starting docker containers...'
                dir('docker'){
                    script {
                        def remote = [:]
                        remote.name = 'runner'
                        remote.host = 'runner'
                        remote.user = 'orkuz'
                        remote.password = '1234'
                        remote.allowAnyHosts = true
                        stage('Remote SSH') {
                            sshPut remote: remote, from: 'compose.yaml', into: '.'
                            sshCommand remote: remote, command: "docker-compose up -d"
                        }
                    }
                }
            }
        }
    }
}