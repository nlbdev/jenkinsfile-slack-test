pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            checkout scm
        }
        
        stage('Build') {
            sh 'echo "Building..." | slack-cli -d test'
            sh 'echo do some building here'
        }
    }
    post {
        always {
            sh 'echo "Finally" | slack-cli -d test'
        }
    }
}
