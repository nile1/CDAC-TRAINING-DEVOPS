pipeline {
    agent any

    environment {
	DOCKERIMAGE = 'hello-world-python:latest'
    }


    stages {
	stage('checkout') {
	    steps {
		git branch: 'main', url:'https://github.com/nile1/CDAC-TRAINING-DEVOPS.git'
		  }

	   }

	   stage('Docker Build') {
	      steps {
		script {
			if (fileExists('Dockerfile')) {
				sh "docker built -t ${env.DOCKER_IMAGE} ."

			} else {
				error "Dockerfile not found in the workspace. Please create one for your python application."

			}

		}
	      }
	   }

	stage('Docker Run') {
              steps {
                sh "docker run --rm ${env.DOCKER_IMAGE}"
		} } }

post {

success {
echo 'Sucess'
}

failure {
echo 'Docker bild or run failed'
} } }
