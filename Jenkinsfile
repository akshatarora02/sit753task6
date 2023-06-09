pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'To build the code, Maven or Gradle can be used'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo ' For unit and integration tests, JUnit, Mockito or Selenium can be used.'
            }
        }
        stage('Code Analysis') {
            steps {
                echo ' For Code Analysis, SonarQube or Checkstyle can be used.'
                }
        }
        stage('Security Scan') {
            steps {
                echo ' For Security Scan, SonarQube or OWASP ZAP can be used.'
            }
            post {  
                always {
                    emailext attachLog: true, body: "Security scan completed with ${currentBuild.currentResult}", recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: "Pipeline ${currentBuild.currentResult} - ${env.JOB_NAME}"
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo ' For deployment to staging, AWS EC2, AWS Elastic Beanstalk, AWS EKS can be used.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo ' For Integration Tests on Staging, Selenium can be used.'
            }
            post {  
                always {
                    emailext attachLog: true, body: "Integration tests completed with ${currentBuild.currentResult}", recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: "Pipeline ${currentBuild.currentResult} - ${env.JOB_NAME}"
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo ' For deployment to Production, AWS EC2, AWS Elastic Beanstalk, AWS EKS can be used.'
            }
        }
    }
}