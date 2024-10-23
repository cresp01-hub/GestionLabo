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
                dir('backend/user-service') {
                    sh 'mvn clean package'
                }
            }
        }
        stage('Build Lab Service') {
            steps {
                dir('backend/lab-service') {
                    sh 'mvn clean package'
                }
            }
        }
        stage('Build Analys Service') {
            steps {
                dir('backend/analysis-service') { // Correction ici
                    sh 'mvn clean package'
                }
            }
        }
        stage('Build API Gateway') {
            steps {
                dir('backend/api-gateway') {
                    sh 'mvn clean package'
                }
            }
        }
        stage('Build Frontend') {
            steps {
                dir('frontend') { // Changez le chemin vers votre projet frontend si nécessaire
                    sh 'npm install' // Installe les dépendances
                    sh 'npm run build' // Ajoutez cette ligne pour construire votre application Angular
                }
            }
        }
        stage('Deploy') {
    steps {
        echo 'Déploiement en cours...'
        // Déployer l'API Gateway
        sh 'docker-compose up --build'
       
       
       

        

       
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
