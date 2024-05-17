pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/JakubWierzchowski/jenkinstest.git', branch: 'main'
            }
        }
    stage('Test') {
        steps {
               sh 'sudo apt install npm'
               sh 'npm test'
            }
        }
    stage('Build') {
            steps {
                // Uruchomienie build w kontenerze Node.js
              
                        sh 'npm run build'
                    }
            
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
