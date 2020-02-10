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
                sh 'docker build -t mauriciopgomes/frango_frito .'
            }
        }
        stage('Push to Registry (Docker-HUB)') {
            steps {
                sh 'docker push mauriciopgomes/frango_frito:latest'
            }
        }
        stage('Run Ansible Playbook') {
            steps {
                sh 'ansible-playbook Playbook.yml'
            }
        }
    }
}