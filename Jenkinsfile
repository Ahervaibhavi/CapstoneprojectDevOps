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