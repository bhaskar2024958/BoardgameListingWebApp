pipeline {
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }

    stages {
         stage('test') {
            steps {
               sh 'mvn test'
            }
        }
        stage('Build') {
            steps {
               sh 'mvn install'
            }
        }
        
    }
}
