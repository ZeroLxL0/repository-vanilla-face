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
                // Se utiliza un contenedor efímero de Python para evaluar el script
                sh 'docker run --rm -v $(pwd):/app -w /app python:3.11-slim python -m unittest test_app.py'
            }
        }
    }
}
