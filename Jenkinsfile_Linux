pipeline {
    // master executor should be set to 0
    agent any
    stages {
        stage('Pull the latest image from hub') {
            steps {
                //sh
                sh "docker pull hozefavakanerwala/selenium-docker"
            }
        }
        stage('Starting selenium grid') {
            steps {
                //sh
                sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage('Run Test'){
            steps {
                sh "docker-compose up search-module book-flight-module"
            }
        }
    }
   post{
        always{
            archiveArtifacts artifacts: 'outputs/**'
            sh "docker-compose down"
        }
   }
}