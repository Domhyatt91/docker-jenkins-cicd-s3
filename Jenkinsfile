pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-2'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Domhyatt91/aws-s3-static-website.git'
            }
        }

        stage('Deploy to S3') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: '309926bf-0435-4ec5-89d1-18d45c4b20bb'
                ]]) {
                    sh '''
                    aws s3 sync . s3://domhyatt91-static-website --delete \
                      --exclude ".git/*" \
                      --exclude "README.md" \
                      --exclude "Jenkinsfile"
                    '''
                }
            }
        }
    }
}
