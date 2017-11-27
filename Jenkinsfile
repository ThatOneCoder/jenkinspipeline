pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                withEnv(['M2_HOME=/usr/local/Cellar/maven/3.3.9/libexec']) {
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
    }
}