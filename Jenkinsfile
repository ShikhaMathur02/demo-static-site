pipeline {
  agent any

  environment {
    AWS_DEFAULT_REGION = 'ap-south-1'
    AWS_ACCESS_KEY_ID = credentials('aws-creds').username
    AWS_SECRET_ACCESS_KEY = credentials('aws-creds').password
  }

  stages {
    stage('Checkout Code') {
      steps {
        git 'https://github.com/ShikhaMathur02/demo-static-site.git'
      }
    }

    stage('Deploy to S3') {
      steps {
        sh '''
          aws s3 cp . s3://localstaticwebsite/ --recursive \
            --region $AWS_DEFAULT_REGION
        '''
      }
    }
  }
}
