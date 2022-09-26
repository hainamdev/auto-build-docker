pipeline {
	agent any
<<<<<<< HEAD
	tool {
		maven 'maven3'
	}
	stages {
		stage('SCM Checkout'){
			steps{
				echo "hello world"
			}
		}
	}
}
=======
	tools {
		maven 'maven3'
	}
	stages {
		stage('Build Maven'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/hainamdev/auto-build-docker']]])
				sh 'mvn clean install'
			}
		}
		stage('Build Docker Image'){
			steps{
				sh 'docker build -t hainamdev/auto-buid-push-docker:1.0.0 .'
			}
		}
		stage('Push DockerHub'){
			steps{
				withDockerRegistry(credentialsId: 'dockerpwd', url: 'https://index.docker.io/v1/') {
				   sh 'docker push hainamdev/auto-buid-push-docker:1.0.0'
				}
			}
		}
	}
}
>>>>>>> 5bc9295f5b576d391e3dbdf54d978320f9314ac4
