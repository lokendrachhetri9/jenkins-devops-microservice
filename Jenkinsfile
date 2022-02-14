//SCRIPTED
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Intregration') {
// 		echo "Intregration Test"
// 	}
//}
//DECLARA
pipeline {
	agent any
	// agent {
    //     docker { image 'node:latest' }
    // }
	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages{
		stage('Checkout') {
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('compile') {
			steps{
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps{
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps{
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
		stage('Package') {
			steps{
				sh 'mvn package -DskipTests'
			}
		}

		stage('Build Docker Image') {
			steps{
				//docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG
				script {
					dockerImage = docker.build("lokendrachhetri9/currency-exchange-devops:$env.BUILD_TAG")
				}
			}
		}

		stage('Push Docker Image') {
			steps{
				script {
					docker.withRegistry('','dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
					
				}
			}
		}
	} 

	post {
		always{
			echo 'This is auto generated regradless of the status'
		}
		success{
			echo 'Pipeline run successful.'
		}
		failure{
			echo 'There have some errors encountred'
		}
	}
}