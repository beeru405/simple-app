pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/beeru405/simple-calculator-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'pip install -r requirements.txt'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    sh 'python -m unittest discover tests'
                }
            }
        }
    }

}
