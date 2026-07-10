// DECLARATIVE
pipeline {
    agent any
    environment {
		jdkHome = tool "myJava11"
        dockerHome = tool "myDocker"
        mavenHome = tool "myMaven"
        PATH = "$jdkHome/bin:$dockerHome/bin:$mavenHome/bin:$PATH"
    }
    stages {
        stage('Checkout') {
            steps {
                sh "mvn --version"
                sh "docker version"
                echo "Build"
                echo "Path - $PATH"
                echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                echo "BUILD_ID - $env.BUILD_ID"
                echo "JOB_NAME - $env.JOB_NAME"
                echo "BUILD_TAG - $env.BUILD_TAG"
                echo "BUILD_URL - $env.BUILD_URL"
            }
        }
        stage('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        stage('Integration Test') {
            steps {
                sh "mvn failsafe:integration-test failsafe:verify"
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