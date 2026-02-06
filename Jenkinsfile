pipeline {
    agent any

    tools {
        // Must match the Maven tool name configured in Jenkins (Manage Jenkins -> Global Tool Configuration)
        maven "M398"
    }

    stages {
        stage("Echo Version") {
            steps {
                sh 'echo Print Maven Version'
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                git 'https://github.com/jglick/simple-maven-project-with-tests.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }

        stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
