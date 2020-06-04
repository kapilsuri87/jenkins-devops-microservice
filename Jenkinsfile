pipeline {
	agent any
	//To get tools defined in global tools configuration we use environment
	environment{
		//To get the path of defined plugin use tool command as below
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		// To add the paths to path variable use path command
		PATH= "$mavenHome/bin:$dockerHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				sh 'mvn --version' 
				sh "docker --version"
				echo "Current Job Name - $env.JOB_NAME"
				echo "Current Build Tag - $env.BUILD_TAG"
				echo "Current Build Url - $env.BUILD_URL"
			}
		}
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				echo "mvn test"
			}
		}
		stage('Integration Test'){
			steps{
				echo "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Mvn package'){
			steps{
				echo "mvn package -DskipTests"
			}
		}
		stage('Build Docker image'){
			steps{
				// Primitive way of creating an docker image is as below
				// "docker build -t kapilsuri2905/currency-conversion:env.BUILD_TAG"
				script {
					dockerImage = docker.build("kapilsuri2905/currency-conversion:env.BUILD_TAG")
				}
			}
		}
		stage('Push Docker image'){
			steps{
				script {
					docker.withRegistry('', 'dockerHub'){
					dockerImage.push();
					dockerImage.push('latest')
					}
				}
			}
		}
	}
}