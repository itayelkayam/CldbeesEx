pipeline {
  agent {
    label 'ec2'
  }
  stages {
    stage('Say Hello') {
      steps {
        echo "Hello ${params.Name}!"
        sh 'java -version'
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
      }
    }

    stage('Testing') {
      failFast true
      parallel {
        stage('ec2') {
          agent {
            label 'ec2'
          }
          steps {
            sh 'echo i am ec2'
            sleep(time: 10, unit: 'SECONDS')
          }
        }

        stage('ec2-2') {
          agent {
            label 'ec2-2'
          }
          steps {
            sh 'echo i am ec2-2'
            sleep(time: 20, unit: 'SECONDS')
          }
        }

      }
    }
      stage('Checkpoint') {
         agent none
         steps {
            checkpoint 'Checkpoint'
         }
      }
      stage('Deploy') {
         agent none
         steps {
            echo 'Deploying....'
         }
      }

  }
  environment {
    MY_NAME = 'Itay'
    TEST_USER = credentials('test-user')
  }
  post {
    aborted {
      echo 'Why didn\'t you push my button?'
    }

  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
}
