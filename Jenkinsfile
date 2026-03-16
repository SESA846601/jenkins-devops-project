pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/SESA846601/jenkins-devops-project'
                echo "Cloning Repo"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-devops-app .'
                echo "Building Docker Image"
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker stop flask-container || true'
                sh 'docker rm flask-container || true'
                sh 'docker run -d -p 5000:5000 --name flask-container flask-devops-app'
                echo "Running Container"
            }
        }

    }
}