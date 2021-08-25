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
                sh 'export MAVEN_HOME=/var/jenkins_home/maven/apache-maven-3.6.3'
                sh 'export PATH=$PATH:$MAVEN_HOME/bin'
                sh 'mvn compile war:war'
//                sh 'java -jar target/*.jar'
            }
        }

    }
}