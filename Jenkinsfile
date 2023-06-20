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
                            sshPut remote: remote, from: 'image_tags.sh', into: '.'
                            sshCommand remote: remote, command: "chmod +x image_tags.sh"
                            sshCommand remote: remote, command: "./image_tags.sh"
                            sshCommand remote: remote, command: "docker compose up -d"
                        }
                    }
                }
            }
        }
    }
}