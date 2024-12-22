pipeline {
    agent any
    tools{
        jdk 'jdk17'
        maven 'Maven3'
    }
    environment{
        SONARQUBE_SERVER = 'Sonar-Scanner'
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

        stage('sonar test') {
          steps {
            withSonarQubeEnv('Sonar-Server') {
              sh ''' $SONARQUBE_SERVER/bin/Sonar-Scanner -Dsonar.projectName=Santa \
              -Dsonar.java.binaries=. \
              -Dsonar.projectKey=Santa '''
            }
          }
        }
    }            
    
}
