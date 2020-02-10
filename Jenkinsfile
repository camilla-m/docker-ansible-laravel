pipeline {
    agent any
    stages {
        stage('Start Notification') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'SLACK_NOTIFICATION_FRANGO_VELOZ', variable: 'SLACK_NOTIFICATION_FRANGO_VELOZ')]) {
                        sh 'curl -X POST -H \'Content-type: application/json\' --data \'{"text":":poultry_leg: Build Frango Frito Iniciado :tada: :tada: :tada:"}\' ${SLACK_NOTIFICATION_FRANGO_VELOZ}'
                    }
                }
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
        stage('End Notification') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'SLACK_NOTIFICATION_FRANGO_VELOZ', variable: 'SLACK_NOTIFICATION_FRANGO_VELOZ')]) {
                        sh 'curl -X POST -H \'Content-type: application/json\' --data \'{"text":":poultry_leg: Build Frango Frito Concluido :tada: :tada: :tada: clica nesse paranaue para ver como ficou http://localhost"}\' ${SLACK_NOTIFICATION_FRANGO_VELOZ}'
                    }
                }
            }
        }
    }
}