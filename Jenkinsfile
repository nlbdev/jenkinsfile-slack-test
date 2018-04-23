#!/usr/bin/env groovy

pipeline {
    agent any
    
    options {
        skipDefaultCheckout()
    }
    
    stages {
        stage('Checkout') {
            steps {
                sh 'echo "Started job \"$JOB_NAME [$BUILD_NUMBER]\". Check console output at $BUILD_URL" | slack-cli -d test || true'
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                sh 'echo do some building here'
                sh 'rm "modules/nlb/book-to-pef/target" -rf'
                sh 'cp "asdfqwer" "modules/nlb/book-to-pef/target" -r'
                sh 'cp "yfyfyf" "maven.log"'
                sh 'touch "modules/nlb/book-to-pef/target/*"'
                sh 'touch "modules/nlb/book-to-pef/target/surefire-reports/*"'
                sh 'touch "maven.log"'
            }
        }
    }
    post {
        always {
            // Run the steps in the post section regardless of the completion status of the Pipeline’s or stage’s run.
            junit "**/target/surefire-reports/*.xml"
            archiveArtifacts artifacts: "modules/nlb/**/*.jar"
            archiveArtifacts artifacts: "modules/nordic/**/*.jar"
            archiveArtifacts artifacts: "**/target/test.log"
        }
        
        failure {
            sh 'tail -n 30 maven.log | slac-cli -d test || true'
            sh 'echo "Build failed" | slack-cli -d test || true'
        }
        
        success {
            // Only run the steps in post if the current Pipeline’s or stage’s run has a "success" status, typically denoted by blue or green in the web UI.
            sh 'echo "Build successful" | slack-cli -d test || true'
        }
    }
}
