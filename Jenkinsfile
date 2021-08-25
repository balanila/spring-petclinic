pipeline{
    agent any
    tools {
        maven 'Maven 3.6.3'
        jdk 'jdk8'
    }
    stage{ ("build")
        steps {
            sh 'mvnw package'
            sh 'java -jar target/*.jar'
            }            
        }
}