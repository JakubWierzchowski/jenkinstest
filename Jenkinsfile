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
                // Instalacja zależności
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                // Budowanie aplikacji
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                // Uruchomienie testów
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                // Uruchomienie aplikacji
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
