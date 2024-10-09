pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                // Clonar el repositorio
                git 'https://github.com/LuizMv80/Jenkins-lab.git'
            }
        }
        
        stage('Build Docker image') {
            steps {
                // Construir la imagen de Docker
                sh 'docker build -t my-web-app .'
            }
        }
        
        stage('Deploy Docker container') {
            steps {
                // Detener el contenedor si está corriendo
                sh '''
                if [ $(docker ps -q -f name=my-web-app) ]; then
                  docker stop my-web-app
                  docker rm my-web-app
                fi
                '''
                // Levantar el contenedor de Docker
                sh 'docker run -d --name my-web-app -p 80:80 my-web-app'
            }
        }
    }
}

