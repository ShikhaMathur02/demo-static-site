pipeline {
  agent any

  environment {
    AWS_DEFAULT_REGION = 'ap-south-1'
    AWS_CREDENTIALS = credentials('aws-creds') // Jenkins credentials ID
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
          --region $AWS_DEFAULT_REGION \
          --access-key $AWS_CREDENTIALS_USR \
          --secret-key $AWS_CREDENTIALS_PSW
        '''
      }
    }
  }
}
