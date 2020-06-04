pipeline {
	agent any
	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH= "$mavenHome/bin:$dockerHome/bin:$PATH"
	}
	stages{
		stage('Build'){
			steps{
				echo "Build"
				sh 'mvn --version' 
				sh "docker --version"
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