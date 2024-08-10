pipeline {
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }

    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/bhaskar2024958/BoardgameListingWebApp.git'
            }
        }
        stage('Build') {
            steps {
               sh 'mvn install'
            }
        }
        
    }
}
