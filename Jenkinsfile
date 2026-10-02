pipeline {
    agent any
    stages {
        stage ('Clonar Código') {
            steps {
                checkout scm
            }
        }
        stage ('Ejecutar Pruebas Python') {
            steps {
                // Solución al problema de volúmenes compartidos en entornos Docker-in-Docker
                sh '''
                cat <<EOF > Dockerfile
                FROM python:3.11-slim
                WORKDIR /app
                COPY . .
                EOF
                docker build -t python-efimero .
                docker run --rm python-efimero python -m unittest test_app.py
                '''
            }
        }
    }
}
