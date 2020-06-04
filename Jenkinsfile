// SCRIPTED APPROACH - Stahge blocks are opptional
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	// OR
// 	echo "Test"
// 	echo "Deploy"
// }

// Declarative APPROACH
pipeline {
	agent any
	//To use a docker image user agent as docker
	// agent {
    //     docker { image 'maven:3.6.3' }
    // }
	stages{
		stage('Build'){
			steps{
				// sh 'mvn --version' 
				echo "Build"
				echo "Current Build - $env.BUILD_NUMBER"
				echo "Current Job Name - $env.JOB_NAME"
				echo "Current Build Tag - $env.BUILD_TAG"
				echo "Current Build Url - $env.BUILD_URL"
			}
		}
		stage('Test'){
			steps{
				echo "Test"
			}
		}
		stage('Deployment'){
			steps{
				echo "Deploy"
			}
		}
	}
	post{
		always{
			echo "I always run"
		}
		success{
			echo "I only run if build is successfull"
		}
		failure{
			echo "I run when builf fails"
		}
		//changed: When build status changes then this event is triggered
		//unstable: If test cases fails
	}
}