pipeline {
    agent any
    stages {
        stage('Build Aplication') {
            steps {
                sh 'curl -X POST -H \'Content-type: application/json\' --data \'{"text":":poultry_leg: Build Frango Frito Iniciado :tada: :tada: :tada:"}\' https://hooks.slack.com/services/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'
            }
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