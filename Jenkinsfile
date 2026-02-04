pipeline {
    agent any 

    stages {
        
        stage('Clone repository') {
            steps {
                git branch:'main',
                url:'https://github.com/Kameshjustin/Devops_FE_Jenkins_project_3.git'
            }
        }

        stage('Build docker image') {
            steps {
                sh 'docker build -t analog-clock'
            }
        }

        stage('Stop old container') {
            steps {
                sh 'docker rm -f analog-container || true'
            }
        }

        stage('Run new container') {
            steps {
                sh 'docker run -d -p 8080:80 --name analog-container analog-clock'
            }
        }
    }
}