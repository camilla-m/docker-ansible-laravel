pipeline {
    agent any
    stages {
        stage('Notification') {
            steps {
                sh 'curl -X POST -H \'Content-type: application/json\' --data \'{"text":":poultry_leg: Build Frango Frito Iniciado :tada: :tada: :tada:"}\' https://hooks.slack.com/services/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'
            }
        }
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