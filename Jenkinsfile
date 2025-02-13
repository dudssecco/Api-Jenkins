pipeline {
    agent any

    environment {
        // Defina a variável de ambiente para a versão da API
        VERSION = "1.0.0"
        IMAGE_NAME = "meu-api-node"
        DOCKER_REGISTRY = "localhost:5000"  // Defina seu registry Docker, se necessário
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Fazendo checkout do código...'
                git 'https://github.com/dudssecco/Api-Jenkins'  // Substitua com seu repositório
            }
        }

        

    post {
        success {
            echo 'Pipeline executado com sucesso!'
        }
        failure {
            echo 'Pipeline falhou!'
        }
    }
}
