pipeline {
  agent {
    label 'ec2'
  }
  stages {
    stage('Say Hello') {
      steps {
        echo 'Hello World besties!'
        sh 'java -version'
      }
    }

  }
}