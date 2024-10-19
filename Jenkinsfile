pipeline {
    agent any
    tools {
        maven 'maven-3.9.6' // Remplacez par le nom que vous avez donné à votre installation Maven dans Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build User Service') {
            steps {
                dir('backend/user-service') { // Remplacez par le nom du service que vous souhaitez construire
                    sh 'mvn clean install'
                }
            }
        }
        stage('Build Lab Service') {
            steps {
                dir('backend/lab-service') { // Remplacez par le service à construire
                    sh 'mvn clean install'
                }
            }
        }
        stage('Build Analys Service') {
            steps {
                dir('backend/analysis-service') { // Remplacez par le service à construire
                    sh 'mvn clean install'
                }
            }
        }
        stage('Build API Gateway') {
            steps {
                dir('backend/api-gateway') { // Remplacez par le service à construire
                    sh 'mvn clean install'
                }
            }
        }
    }
    stage('Build Frontend') {
            steps {
                dir('frontend') { // Changez le chemin vers votre projet frontend si nécessaire
                    sh 'npm install' // ou la commande que vous utilisez pour construire votre frontend
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Déploiement en cours...'
                // Ajoutez vos étapes de déploiement ici
            }
        }
    }

    post {
        success {
            echo 'Pipeline exécuté avec succès!'
        }
        failure {
            echo 'Le pipeline a échoué!'
        }
    }
}
