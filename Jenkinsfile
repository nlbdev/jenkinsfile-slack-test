pipeline {
    agent any
    
    try {
        stages {
            stage('Checkout') {
                checkout scm
            }
            
            stage('Build') {
                sh 'echo "Building..." | slack-cli -d test'
                sh 'echo do some building here'
            }
        }
    } finally {
        sh 'echo "Finally" | slack-cli -d test'
    }
}
