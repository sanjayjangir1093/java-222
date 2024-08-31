pipeline {
	agent any
	stages {
		stage ("pull code from git repo"){
		
			steps{
				git branch: 'main', url: 'https://github.com/sanjayjangir1093/java-222.git'
			}
		}
		stage ("Build the code"){
			steps{
				sh 'sudo mvn dependency:purge-local-repository'
                                sh 'sudo mvn install'
			}
		}
		stage ("Building docker image"){
			steps{
				sh 'sudo docker build -t jo:$BUILD_TAG .'
		
	         	}
         	}
       }
}
