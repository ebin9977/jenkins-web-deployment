
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting source code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Preparing Web Application'
                echo 'Build completed successfully'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application'
                sh 'test -f index.html'
                echo 'Application test successful'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website to Apache server'
                sh '''
                    cp "$WORKSPACE/index.html" /var/www/html/index.html
                    chmod 644 /var/www/html/index.html
                '''
                echo 'Deployment completed successfully'
            }
        }
    }

    post {
        success {
            echo 'Website deployed successfully!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
