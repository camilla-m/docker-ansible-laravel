pipeline {
    agent any
    stages {
        stage('Build Aplication') {
            steps {
                sh 'docker build -t mauriciopgomes/frago_frito .'
            }
        }
        stage('Push to Registry (Docker-HUB)') {
            steps {
                sh 'docker push mauriciopgomes/frago_frito:latest'
            }
        }
        stage('Run Ansible Playbook') {
            steps {
                sh 'ansible-playbook Playbook.yml'
            }
        }
    }
}

    post {
        always {
            cleanWs()
        }
    }
}