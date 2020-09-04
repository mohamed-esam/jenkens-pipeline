pipeline {
  agent any
  stages {
    stage('AWS Credentials') {
      steps {
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIAUYQLQG3C32YX6WYM', credentialsId: 'blueocean', secretKeyVariable: '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']]) {
        sh """  
               mkdir -p ~/.aws
               echo "[default]" >~/.aws/credentials
               echo "[default]" >~/.boto
               echo "aws_access_key_id = ${AKIAUYQLQG3C32YX6WYM}" >>~/.boto
               echo "aws_secret_access_key = ${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}">>~/.boto
               echo "aws_access_key_id = ${AKIAUYQLQG3C32YX6WYM}" >>~/.aws/credentials
               echo "aws_secret_access_key = ${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}">>~/.aws/credentials
        """
        }
      }
    }
    stage('Create EC2 Instance') {
      steps {
        ansiblePlaybook playbook: 'main.yaml', inventory: 'inventory'
      }
    }
  }
}
