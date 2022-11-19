pipeline {
	agent any
	stages {
		stage ('Checkout') {
			steps {
				git branch:'main', url: 'https://github.com/junjie167/ict3x03-AssuranceBank.git'
				}
				}
		stage('Code Quality Check via SonarQube') {
			steps {
				script {
					def scannerHome = tool 'SonarQube';
					withSonarQubeEnv('SonarQube') {
						sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=3x03 -Dsonar.sources=."
						}
					}
				}
			}
}
post {
	always {
		recordIssues enabledForFailure: true, tool: sonarQube()
		}
	}
}