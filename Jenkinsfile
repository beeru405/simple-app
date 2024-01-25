pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests using Maven
                    def testResult = sh(script: 'mvn test', returnStatus: true)
                    
                    // Check the test results and mark the build as failed if any test failed
                    if (testResult != 0) {
                        currentBuild.result = 'FAILURE'
                        error('Tests failed. Marking the build as FAILURE.')
                    }
                }
            }
        }
    }
}
