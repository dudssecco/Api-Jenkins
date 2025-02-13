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

        stage('Instalar Dependências') {
            steps {
                echo 'Instalando dependências...'
                sh 'npm install'
            }
        }

        stage('Rodar Testes') {
            steps {
                echo 'Executando os testes...'
                sh 'npm test'  // Substitua pelo comando adequado para os testes da sua API
            }
        }

        stage('Construir Imagem Docker') {
            steps {
                echo 'Construindo a imagem Docker...'
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:${VERSION}")
                }
            }
        }

        stage('Rodar API em Docker') {
            steps {
                echo 'Rodando a API dentro de um container Docker...'
                script {
                    dockerImage.run("-d -p 3000:3000")  // Substitua a porta conforme sua configuração
                }
            }
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
