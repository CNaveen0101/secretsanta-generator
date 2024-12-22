pipeline {
    agent any
    tools{
        jdk 'jdk17'
        maven 'Maven3'
    }
    environment{
        SCANNER_HOME= tool 'Sonar-Scanner-tool'
    }
    stages {
        stage('git-checkout') {
            steps {
              git 'https://github.com/CNaveen0101/secretsanta-generator'
            }
        }

        stage('Code-Compile') {
          steps {
            sh "mvn compile"
          }
        }

        stage('Code-Package') {
          steps {
            sh "mvn clean package"
          }
        }

        stage('Sonar Analysis') {
            steps {
               withSonarQubeEnv('Sonar-Server'){
                   sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Santa \
                   -Dsonar.java.binaries=. \
                   -Dsonar.projectKey=Santa '''
               }
            }
        }
    }            
    
}
