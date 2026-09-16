pipeline {
    agent any

    environment {
        APP_NAME = 'jenkins-demo'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh './app/app.sh'
            }
        }

        stage('Test') {
            steps {
                sh './tests/test.sh'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }

            steps {
                echo "Deploying ${APP_NAME}..."
                echo "🚀 Application deployed successfully!"
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline completed successfully!"
        }

        failure {
            echo "❌ Pipeline failed!"
        }
    }
}
