pipeline {
  agent {
    label 'ec2'
  }
  stages {
    stage('Say Hello') {
      steps {
        echo "Hello ${MY_NAME}!"
        sh 'java -version'
      }
    }

  }
  environment {
    MY_NAME = 'Itay'
  }
}