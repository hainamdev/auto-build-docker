pipeline {
	agent any
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
