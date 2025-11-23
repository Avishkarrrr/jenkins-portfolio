pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Build step (nothing to compile for static site)...'
                // For static HTML/CSS, this might just be validation in future
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying files to web directory...'
                sh '''
                    DEPLOY_DIR=/var/www/html/portfolio
                    rm -rf $DEPLOY_DIR/*
                    cp -r * $DEPLOY_DIR/
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
