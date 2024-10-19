pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Vérifie le code source depuis GitHub
                checkout scm
            }
        }
        stage('Build Backend') {
            steps {
                dir('backend') {
                    // Construire le backend avec Maven
                    sh 'mvn clean install'
                }
            }
        }
        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    // Construire le frontend avec npm
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                // Ajoutez ici les étapes pour déployer votre application
                echo 'Déploiement de l’application...'
            }
        }
    }
    post {
        success {
            echo 'Pipeline exécuté avec succès !'
        }
        failure {
            echo 'Échec de l’exécution du pipeline.'
        }
    }
}
