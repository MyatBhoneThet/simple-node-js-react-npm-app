pipeline {
  agent any

  environment {
    CI = 'true'
  }

  tools {
    nodejs 'node18'
  }

  stages {
    stage('Install') {
      steps {
        sh 'node -v'
        sh 'npm -v'
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh 'chmod +x jenkins/scripts/test.sh'
        sh './jenkins/scripts/test.sh'
      }
    }

    stage('Deliver') {
      steps {
        sh 'chmod +x jenkins/scripts/*.sh'
        sh './jenkins/scripts/deliver.sh'
        input message: 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}
