pipeline {
    agent {
        label 'sanjay'
    }
    environment {
        MY_VAR = 'Hello, World!'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'mkdir build'
                sh 'cp src/* build/'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'java -jar test.jar'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'ssh deploy@remote-server "mkdir -p /opt/deploy"'
                sh 'scp build/* deploy@remote-server:/opt/deploy/'
            }
        }
        stage('Cleanup') {
            steps {
                echo 'Cleaning up...'
                sh 'rm -rf build'
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished'
        }
        success {
            echo 'Pipeline succeeded'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
