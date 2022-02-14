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
	stages{
		stage('Build') {
			steps{
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Test') {
			steps{
				echo "Test"
			}
		}
		stage('Intregration Test') {
			steps{
				echo "Intregration Test"
			}
		}
	} 

	post {
		always{
			echo 'I am awesome. Run always'
		}
		success{
			echo 'I run when you are successful'
		}
		failure{
			echo 'I run when you are failure.'
		}
	}
}