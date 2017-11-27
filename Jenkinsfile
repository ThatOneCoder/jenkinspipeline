pipeline {
    agent any
    stages{
        
        stage('Build'){
            steps {
                withMaven(maven: 'localMaven') {
                    sh 'mvn clean package'
                }
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        
        stage ('Deploy to Staging') {
            steps {
                build job: 'Deploy-to-staging'
            }
        }

        stage ('Deploy to Production') {
            steps {
                timeout(time:5, unit:'DAYS') {
                    input message: 'Approve PROD Deployment?'
                }
            }
            post {
                success {
                    echo 'Code Deployed to Production'
                }
                failure {
                    echo 'Code Deployment to Production FAILED'
                }
            }
        }
    }
}