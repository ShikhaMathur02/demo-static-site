pipeline {
  agent any

  environment {
    AWS_DEFAULT_REGION = 'us-east-1'
  }

  stages {
    stage('Checkout Code') {
      steps {
        git 'https://github.com/ShikhaMathur02/demo-static-site.git'
      }
    }

    stage('Deploy to S3') {
      steps {
        withCredentials([
          usernamePassword(
            credentialsId: 'aws-creds',
            usernameVariable: 'AWS_ACCESS_KEY_ID',
            passwordVariable: 'AWS_SECRET_ACCESS_KEY'
          )
        ]) {
          bat """
           set AWS_ACCESS_KEY_ID=%AWS_ACCESS_KEY_ID%
           set AWS_SECRET_ACCESS_KEY=%AWS_SECRET_ACCESS_KEY%
           aws s3 cp . s3://localstaticbucket/ --recursive --region %AWS_DEFAULT_REGION%
          """

        }
      }
    }
  }
}
