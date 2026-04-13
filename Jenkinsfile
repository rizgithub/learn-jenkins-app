pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
    post {
        always {
            echo 'Always'
        }
        success {
            echo 'Success'
        }
        failure {
            echo 'Failure'
        }
    }
}