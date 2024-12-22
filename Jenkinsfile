pipeline {
    agent any
    tools{
        jdk 'jdk17'
        maven 'Maven3'
    }
    environment{
        SONARQUBE_SERVER = 'Sonar-Server'
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
              sh "mvn sonar:sonar \
              -Dsonar.projectKey=secretsanta-generator \
              -Dsonar.host.url=${192.168.1.9:9000} \
              -Dsonar.login=${Sonar-Cred}"
            }
          }
        }
    }            
    
}
