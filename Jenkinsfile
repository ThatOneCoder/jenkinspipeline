pipeline {
    agent any
    
    stages{
            stage('Build'){
                steps {
                    def mvnHome = tool 'M3'
                    sh "${mvnHome}/bin/mvn clean package"
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