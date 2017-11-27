pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn --version'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}