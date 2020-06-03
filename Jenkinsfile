// SCRIPTED APPROACH - Stahge blocks are opptional
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	// OR
// 	echo "Test"
// 	echo "Deploy"
// }

Declarative APPROACH
pipeline {
	agent any
	stages{
		stage('Build'){
			steps{
				echo "Build"
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
}