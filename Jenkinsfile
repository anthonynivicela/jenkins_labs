pipeline {
    agent any

    stages {
        stage('Clonar proyecto') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/anthonynivicela/jenkins_labs.git',
                        credentialsId: 'github-token' // 👈 este es el ID que registraste en Jenkins
                    ]]
                ])
            }
        }

       stage('Instalar dependencias') {
    steps {
        bat 'C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python311\\Scripts\\pip.exe install -r mlops\\Caso1\\requirements.txt'

    }
}

stage('Entrenar modelo') {
    steps {
        bat '"C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python311\\python.exe" mlops\\Caso1\\train_model.py'
    }
}

stage('Desplegar API') {
    steps {
        bat 'start /b uvicorn mlops.Caso1.api:app --host 0.0.0.0 --port 8000'
    }
}
    }
}
