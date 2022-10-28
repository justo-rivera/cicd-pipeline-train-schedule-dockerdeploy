pipeline {
	stages {
    	stage('Build') {
        sh './gradlew build'
        sh './gradlew npm_start'
        }
    }
}
