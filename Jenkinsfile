pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh '''
                ls -la 
                node -v
                npm -v
                npm ci
                npm run build
                ls -la
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Executing tests...'
                sh '''
                ls -la
                test -f build/index.html
                npm test
                ls -la
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh '''
                
                '''
            }
        }
    }

    environment {
        NODE_ENV = 'production'
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