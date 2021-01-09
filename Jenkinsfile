pipeline {
    // master executor should be set to 0
    agent any
    stages {
        stage('Pull the latest image from hub') {
            steps {
                //sh
                bat "docker pull hozefavakanerwala/selenium-docker"
            }
        }
        stage('Starting selenium grid') {
            steps {
                //sh
                bat "docker-compose up -d hub chrome firefox"
            }
        }
        stage('Run Test'){
            steps {
                bat "docker-compose up search-module book-flight-module"
            }
        }
    }
   post{
        always{
            archiveArtifacts artifacts: 'output/**'
            bat "docker-compose down"
        }
   }
}