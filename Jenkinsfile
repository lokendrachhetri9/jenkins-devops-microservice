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
    //     docker { image 'maven:3.6.3' }
    // }
	stages{
		stage('Build') {
			steps{
				// sh 'mvn --version'
				echo "Build"
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
