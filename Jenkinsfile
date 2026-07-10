// DECLARATIVE
pipeline{
	agent any
	environment {
		dockerHome = tool "myDocker"
		mavenHome = tool "myMaven"
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	// agent { docker { image 'maven:3.6.3' } }
	stages {
		stage('Checkout') {
			steps{
				sh "mvn --version"
				sh "docker version"
				echo "Build"
				echo "Path - $Path"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile') {
			steps{
				echo "mvn clean compile"
			}
		}
		stage('Test') {
			steps{
				echo "mvn Test"
			}
		}
		stage('Integration Test') {
			steps{
				echo "mvn failsafe:integration-test failsafe:verify"
			}
		}
	} 
	
	post {
		always {
			echo "Runs Always"
		}
		success {
			echo "Runs only if Success"
		}
		failure {
			echo "Runs only if Failure"
		}
	}
}
