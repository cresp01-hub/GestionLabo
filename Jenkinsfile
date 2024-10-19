pipeline {
    agent any

    tools {
        maven 'maven-3.9.6' // Remplacez par le nom de votre installation Maven dans Jenkins
    }

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Build Backend') {
            steps {
                dir('backend') { // Changez le chemin vers votre projet backend si nécessaire
                    sh 'mvn clean install'
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
