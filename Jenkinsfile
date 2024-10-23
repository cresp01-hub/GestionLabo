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
        sh '''
        docker stop api-gateway || true
        docker rm api-gateway || true
        docker run -d --name api-gateway -p 8080:8080 api-gateway:latest
        '''

        // Déployer le User Service
        sh '''
        docker stop user-service || true
        docker rm user-service || true
        docker run -d --name user-service -p 8081:8080 user-service:latest
        '''

        // Déployer le frontend 
        sh '''
        docker stop frontend || true
        docker rm frontend || true
        docker run -d --name frontend -p 4200:80 frontend:latest
        '''
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
