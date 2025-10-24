pipeline {
    agent any
    stages {
stage('Clone') {
    steps { 
        git credentialsId: 'github-creds', url: 'https://github.com/Chama-123/python.git'
    }
}
        stage('Build Docker') {
            steps { sh 'docker build -t python-employee-app .' }
        }
        stage('Run Tests') {
            steps { sh 'pytest tests/' }
        }
        stage('Deploy Docker') {
            steps {
                sh 'docker stop python-employee-app || true'
                sh 'docker run -d -p 8000:8000 --name python-employee-app python-employee-app'
            }
        }
    }
}

