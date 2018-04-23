pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building..." | slack-cli -d test'
                sh 'echo do some building here'
                sh 'touch "modules/nlb/book-to-pef/target/surefire-reports/*"'
            }
        }
    }
    post {
        always {
            junit "**/target/surefire-reports/*.xml"
            sh 'echo "Finally" | slack-cli -d test'
        }
    }
}
