pipeline {
    agent any
    tools {
        maven 'maven 3.6.3'
        jdk 'jdk 8'
    }
    stages {
        stage ('Build') {
            steps {
                sh 'echo "BUILD STEP"'
                sh 'export MAVEN_HOME=/var/jenkins_home/maven/apache-maven-3.6.3'
                sh 'export PATH=$PATH:$MAVEN_HOME/bin'
                sh 'mvn compile war:war'
//                sh 'java -jar target/*.jar'
            }
        }
        stage ('SonarQube') {
            environment {
                    scannerHome = tool 'SonarQube'
            steps {
                sh "echo SonarQube Step"
                withSonarQubeEnv('sonarqube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }

                timeout(time: 10, unit: 'MINUTES') {
                    timeout(time: 10, unit: 'MINUTES')
                }

                }
                
            }
        }
        stage ('Upload to jFrog') {
            steps {
                rtUpload (
                    serverId: 'default-maven-local',
                    spec: '''{
                        "files": [
                            {
                             "pattern": "/var/jenkins_home/workspace/spring-petclinic_pipeline/target/spring-petclinic-2.4.5.war",
                             "target": "default-maven-virtual/"
                            }
                        ]
                    }''',
                )
            }
        }

    }
}