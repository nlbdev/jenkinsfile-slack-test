pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building..." | slack-cli -d test'
                sh 'echo do some building here'
                sh 'rm "modules/nlb/book-to-pef/target" -rf'
                sh 'cp "asdfqwer" "modules/nlb/book-to-pef/target" -r'
                sh 'touch "modules/nlb/book-to-pef/target/*"'
                sh 'touch "modules/nlb/book-to-pef/target/surefire-reports/*"'
            }
        }
    }
    post {
        always {
            junit "**/target/surefire-reports/*.xml"
            sh 'echo "Finally" | slack-cli -d test'
            sh 'printenv'
        }
    }
}
