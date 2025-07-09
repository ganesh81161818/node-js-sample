pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/ganesh81161818/node-js-sample.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def myImage = docker.build('my-node-app')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    docker.image('my-node-app').run('-p 3000:3000')
                }
            }
        }
    }
}
