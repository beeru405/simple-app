pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Use Maven to build the project
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run Maven test phase
                sh 'mvn test'
            }
        }
    }
}



=====================================
pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'calc-app'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
                }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE, "--file=Dockerfile .")
                }
            }
        }

        stage('Deploy to Docker') {
            steps {
                script {
                    docker.withRegistry('https://your-docker-registry', 'docker-registry-credentials') {
                        docker.image(DOCKER_IMAGE).push()
                    }
                }
            }
        }
    }
}
