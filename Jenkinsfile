pipeline {
    agent any
    tools{
        jdk 'jdk17'
        maven 'Maven3'
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

        stage('Code-Compile') {
          steps {
            sh "mvn clean package"
          }
        }
    }            
    
}
