pipeline {
    // master executor should be set to 0
    agent any
    stages {
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
        stage('Bring grid down') {
            steps {
                //sh
                bat "docker-compose down"
            }
        }
   }