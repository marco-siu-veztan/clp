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
                dir ('device-api'){
                    script {
                        dockerImage = docker.build registry+":$BUILD_NUMBER"
                    }
                }
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
        stage('Deploy') {
            steps {
                sh "kubectl apply -f nodejs-deploy.yaml"
            }
        }
    }
}
