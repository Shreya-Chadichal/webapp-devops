pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t webapp:v1 .
                '''
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh '''
                cd ansible
                ansible-playbook -i inventory deploy.yml
                '''
            }
        }
    }
}
