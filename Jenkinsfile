pipeline {
    agent any
    environment {
        PATH = "$PATH:/usr/local/go/bin"
        NEXUS_URL = 'http://<192.168.128.43>:8081/repository/go-binaries/'
        NEXUS_CREDS = credentials('nexus-credentials')
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AndreevAleksandr/8-02hw'
            }
        }
        stage('Test') {
            steps {
                sh 'go build -o myapp main.go'
            }
        }
        stage('Upload to Nexus') {
            steps {
                script {
                    sh """
                    curl -v -u ${NEXUS_CREDS_USR}:${NEXUS_CREDS_PSW} --upload-file ./myapp \
                    ${NEXUS_URL}/myapp
                    """
                }
            }
    }
}
