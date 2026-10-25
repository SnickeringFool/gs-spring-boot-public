pipeline {
    agent any
 
    tools {
        maven 'maven'   // must match the name in Manage Jenkins > Tools
    }
 
    stages {
        stage('Build') {
            steps {
			dir('complete') {
                sh 'mvn -B clean package'
            }
	}
}
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'complete/target/*.jar', fingerprint: true
            }
        }
    }
 
    post {
        success { echo 'Build succeeded, jar archived.' }
        failure { echo 'Build failed, check the console output.' }
    }
}
