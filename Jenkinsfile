pipeline {
    agent any
    tools {nodejs "NodeJS"}
    environment {
        registry = "marcosiu/clp"
        registryCredential = 'dockerhub'
        dockerImage = ''
    }
    stages {
        stage('Tests') {
            steps {
                dir ('device-api'){
                        echo 'Building..'
                        sh 'npm install'
                        // echo 'Testing..'
                        // sh 'npm test'
                }
            }
        }
        stage('Build image') {
            steps {
                sh "docker build -t ${registry}:${BUILD_NUMBER} ."
            }
        }

        stage('Push image') {
            steps {
                script {
                    docker.withRegistry('', registryCredential) {
                    dockerImage.push()
                    }
                }
            }
        }
    }
}
