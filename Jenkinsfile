pipeline {
    agent any

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
    }
}
