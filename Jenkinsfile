pipeline {
    agent any

    stages {

        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Build docker image') {
            steps {
                sh 'docker build -t analog-clock .'
            }
        }

        stage('Stop old container') {
            steps {
                sh 'docker rm -f analog-container || true'
            }
        }

        stage('Run new container') {
            steps {
                sh 'docker run -d -p 8081:80 --name analog-container analog-clock'
            }
        }
    }
}
