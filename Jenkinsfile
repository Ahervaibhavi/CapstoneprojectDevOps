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
    }
}