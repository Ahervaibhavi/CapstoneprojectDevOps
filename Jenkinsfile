pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Applications') {
            steps {
                echo 'Building application components...'

                dir('frontend') {
                    bat 'npm install'
                }

                dir('product-service') {
                    bat 'npm install'
                }

                dir('order-service') {
                    bat 'npm install'
                }

                dir('inventory-service') {
                    bat 'npm install'
                }
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