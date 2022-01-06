pipeline {
    agent {
        docker { image 'amazon/aws-cli' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'aws --version'
            }
        }
    }
}
