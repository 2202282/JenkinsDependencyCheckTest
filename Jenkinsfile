pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git url: 'https://github.com/2202282/JenkinsDependencyCheckTest', branch: 'master'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP-Dependency-Check'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
