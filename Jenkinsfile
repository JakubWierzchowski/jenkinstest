pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
       stage('Test') {
            steps {
                script {
                    docker.image('node:14').inside {
                  
                        sh 'npm test'
                    }
                }
                echo 'Success'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}