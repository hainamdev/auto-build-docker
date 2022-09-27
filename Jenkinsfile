pipeline {
	agent any
	tools {
		maven 'maven3'
	}
	stages {
		stage('Clone repo'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/hainamdev/auto-build-docker']]])
				sh 'mvn clean install'
			}
		}
		stage('Build Maven'){
			steps{
				sh 'mvn clean install'
			}
		}
		stage('Build Docker Image'){
			steps{
					script {
					    sh 'docker build -t hainamdev/demo . '
					}
			}
		}
		
	}
}
