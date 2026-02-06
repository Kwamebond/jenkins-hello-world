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
                script {
                    for (int i = 0; i < 60; i++) {
                        echo "${i + 1}"
                        sleep 1
                    }
                }
                sh 'mvn test'
            }
        }
    }
}
