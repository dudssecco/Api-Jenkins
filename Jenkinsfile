pipeline {
    agent any

    environment {
        // Variáveis de ambiente, como porta da API ou credenciais, se necessário
        API_PORT = '3000'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Fazendo checkout do código...'
                git 'https://github.com/dudssecco/Api-Jenkins'  // Se for GitHub
                // Ou use 'dir("/caminho/para/o/repo")' se for local
            }
        }

        stage('Instalar dependências') {
            steps {
                echo 'Instalando dependências...'
                sh 'npm install'  // Caso sua API seja em Node.js
                // Ou 'pip install -r requirements.txt' para Python, etc.
            }
        }

        stage('Rodar Testes') {
            steps {
                echo 'Executando testes...'
                // sh 'npm test'  // Substitua por seu comando de teste
            }
        }

        stage('Rodar API') {
            steps {
                echo 'Iniciando a API...'
                sh 'npm start &'  // Ou o comando específico para iniciar sua API
            }
        }

        stage('Verificar API') {
            steps {
                echo 'Verificando se a API está rodando...'
                // Aqui você pode rodar um comando curl para verificar se a API está no ar
                sh 'curl http://localhost:${API_PORT}/status'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executada com sucesso!'
        }
        failure {
            echo 'Pipeline falhou!'
        }
    }
}
