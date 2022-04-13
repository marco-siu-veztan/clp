pipeline {
    agent any
    tools {nodejs "NodeJS"}
    stages {
        stage('Tests') {
            steps {
                dir ('device-api'){
                        echo 'Building..'
                        sh 'npm install'
                        echo 'Testing..'
                        sh 'npm test'
                }
            }
        }
    }
}
