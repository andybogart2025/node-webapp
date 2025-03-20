pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                script {
                    docker.build("node-webapp:${env.BUILD_ID}")
                }
            }
        }
        
        stage('Run') {
            steps {
                script {
                    docker.image("node-webapp:${env.BUILD_ID}").run('-p 3000:3000 --name node-webapp -d')
                }
            }
        }
    }

