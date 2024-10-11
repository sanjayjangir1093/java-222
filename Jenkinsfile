pipeline {
    agent {
        label 'jenki'
    }
    environment {
        MY_VAR = 'Hello, World!'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'mkdir build'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'java -jar ${WORKSPACE}/test/test.jar'
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
