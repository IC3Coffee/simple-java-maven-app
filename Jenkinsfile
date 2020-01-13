pipeline {
    agent any

    options {
        skipStagesAfterUnstable()
    }

    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -e -DskipTests clean package' 
            }
        }
	stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
	stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
            }
        }
    }
    post {
        success {
            archiveArtifacts 'target/my-app-1.0-SNAPSHOT.jar'
        }
    }
}
