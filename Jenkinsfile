pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Docker Check') {
            steps {
                bat 'docker --version'
            }
        }

        stage('Build Docker Images') {
            steps {
                bat 'docker build -t ecommerce-frontend ./frontend'
                bat 'docker build -t ecommerce-product-service ./product-service'
                bat 'docker build -t ecommerce-order-service ./order-service'
                bat 'docker build -t ecommerce-inventory-service ./inventory-service'
            }
        }

        stage('Docker Hub Push') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USERNAME',
                    passwordVariable: 'DOCKER_PASSWORD'
                )]) {

                    bat 'echo %DOCKER_PASSWORD% | docker login -u %DOCKER_USERNAME% --password-stdin'

                    bat 'docker tag ecommerce-frontend %DOCKER_USERNAME%/ecommerce-frontend:latest'
                    bat 'docker tag ecommerce-product-service %DOCKER_USERNAME%/ecommerce-product-service:latest'
                    bat 'docker tag ecommerce-order-service %DOCKER_USERNAME%/ecommerce-order-service:latest'
                    bat 'docker tag ecommerce-inventory-service %DOCKER_USERNAME%/ecommerce-inventory-service:latest'

                    bat 'docker push %DOCKER_USERNAME%/ecommerce-frontend:latest'
                    bat 'docker push %DOCKER_USERNAME%/ecommerce-product-service:latest'
                    bat 'docker push %DOCKER_USERNAME%/ecommerce-order-service:latest'
                    bat 'docker push %DOCKER_USERNAME%/ecommerce-inventory-service:latest'
                }
            }
        }
    }
}