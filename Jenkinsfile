pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            checkout scm
        }
        
        stage('Build') {
            try {
                sh 'echo "Building..." | slack-cli -d test'
                sh 'echo do some building here'
            } finally {
                sh 'echo "Finally" | slack-cli -d test'
            }
        }
    }
}
