pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { git 'https://github.com/AndreevAleksandr/8-02hw' }
        }
        stage('Test') {
            steps { sh 'go test ./...' }
        }
        stage('Build Docker') {
            steps { sh 'docker build -t my-go-app .' }
        }
    }
}
