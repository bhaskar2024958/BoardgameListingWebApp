pipeline {
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        stage('git-checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/your-repo.git'
            }
        }

        stage('Code-Compile') {
            steps {
                sh "mvn clean compile"
            }
        }


        stage('Package') {
            steps {
                sh "mvn clean package"
            }
        }
       

        stage('Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
					sh ''' 
                    $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Devops-CICD \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=Devops-CICD 
                    '''
                }
            }
        }

        stage('Quality Gate Check') {
            steps {
               waitForQualityGate abortPipeline: false
            }
        }
        
    }
}
