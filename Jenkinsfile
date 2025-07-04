pipeline {
  agent any

  environment {
    AWS_DEFAULT_REGION = 'ap-south-1'
  }

  stages {
    stage('Checkout Code') {
      steps {
        git 'https://github.com/ShikhaMathur02/demo-static-site.git'
      }
    }

    stage('Deploy to S3') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'aws-creds', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY')]) {
          sh '''
            aws s3 cp . s3://localstaticwebsite/ --recursive \
              --region $AWS_DEFAULT_REGION
          '''
        }
      }
    }
  }
}
