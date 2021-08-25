pipeline {
    agent any
    tools {
        maven 'maven 3.6.3'
        jdk 'jdk 8'
    }
    stages {
        stage ('Build') {
            steps {
                sh 'echo STEP'
                sh 'mvnw package'
                sh 'java -jar target/*.jar'
            }
        }

    }
}