pipeline {
	agent any
	tools {
		maven 'my-maven'
		jdk 'java-jdk'
	}
	stages {
		stage('Clone')
		{
			steps
			{
			    git url:'https://github.com/shreya2616/employee-service.git', branch:'master'
			}
		}
		stage('Build')
		{
			steps
			{
			    bat "mvn clean install -DskipTests"
			}
		}
		stage('Test')
		{
			steps
			{
			    bat "mvn test"
			}
		}
		stage('Deploy')
		{
			steps
			{
			    bat "docker rm -f employee-container"
			    bat "docker rmi -f employee-image"
			    bat "docker build -t employee-image ."
			    bat "docker run -p 8082:8082 -d --name employee-container employee-image"
			}
		}
	}
}