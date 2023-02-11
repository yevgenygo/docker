pipeline {
	environment {
		registry = "jeniago/devops_course" 
		registryCredential = 'cred'
		dockerImage = ''
	}
	stage('build and push image') {
	    steps {
			script {
				dockerImage = docker.build registry + "$BUILD_NUMBER"
                docker.withRegistry('', registryCredential) {
                dockerImage.push()
            }
        }
    }
	post {
         always {
            bat "docker rmi $registry:$BUILD_NUMBER" // delete the local image at the end
		}	
	}
}