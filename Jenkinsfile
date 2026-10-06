pipeline {
    agent any
    tools {
        maven 'maven-3.9.16'
    }
    stages {
        stage('Initialize') {
            steps {
                echo 'Starting the build sequence'
                sh 'mvn --version'
            }
        }
        stage('Compile and unit test') {
            steps {
                echo 'COmpiling the code'
                sh 'mvn clean test'
            }
            post {
                success {
                    junit '**/target/surefire-reports/*.xml'
                }
                failure {
                    echo 'Unit test failed. Please check the reports for the details'
                }
            }
        }
    }
}