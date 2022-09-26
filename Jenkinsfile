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
				withDockerRegistry(credentialsId: 'docker-pwd', url: 'https://index.docker.io/v1/') {
				    sh 'docker build -t hainamdev/auto-buid-push-docker .'
				}
			}
		}
		stage('Push DockerHub'){
			steps{
				withDockerRegistry(credentialsId: 'docker-pwd', url: 'https://index.docker.io/v1/') {
				    sh 'docker push hainamdev/auto-buid-push-docker .'
				}
			}
		}
	}
}
