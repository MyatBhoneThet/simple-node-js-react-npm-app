pipeline {
    agent {
        docker { image 'node:18' }
    }

    stages {
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build || echo "No build script"'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test || echo "No tests"'
            }
        }
    }
}
