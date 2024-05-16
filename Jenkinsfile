pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pobranie kodu z repozytorium
                git url: 'https://github.com/JakubWierzchowski/jenkinstest.git', branch: 'main'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Uruchomienie npm install w kontenerze Node.js
                script {
                    docker.image('node:14').inside {
                        sh 'npm install'
                    }
                }
            }
        }
        stage('Build') {
            steps {
                // Uruchomienie build w kontenerze Node.js
                script {
                    docker.image('node:14').inside {
                        sh 'npm run build'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                // Uruchomienie testów w kontenerze Node.js
                script {
                    docker.image('node:14').inside {
                        sh 'npm test'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                // Uruchomienie aplikacji za pomocą docker-compose
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        always {
            // Wykonywane zawsze, np. czyszczenie zasobów
            cleanWs()
        }
        success {
            // Wykonywane po udanym pipeline
            echo 'Pipeline zakończony sukcesem!'
        }
        failure {
            // Wykonywane po nieudanym pipeline
            echo 'Pipeline zakończony niepowodzeniem.'
        }
    }
}
