pipeline {
    agent {
        label 'dotnet'
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
