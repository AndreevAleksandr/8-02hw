pipeline {
    agent any
    environment {
        PATH = "$PATH:/usr/local/go/bin"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AndreevAleksandr/8-02hw'
            }
        }
        stage('Test') {
            steps {
                sh 'go test ./...'
            }
        }
        stage('Build Docker') {
            steps {
                sh 'docker build -t my-go-app .'
            }
        }
    }
}
