pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                sh 'echo "Building..." | slack-cli -d test'
                sh 'echo do some building here'
            }
        }
    }
    post {
        always {
            sh 'pwd'
            sh 'find'
            junit "**/target/surefire-reports*.xml"
            sh 'echo "Finally" | slack-cli -d test'
        }
    }
}
