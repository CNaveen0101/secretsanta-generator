pipeline {
    agent any
    tools{
        jdk 'jdk17'
        maven 'maven3'

    stages {
        stage('git-checkout') {
            steps {
                sh "Code checkout Passed"
            }
        }

        stage('Code-Compile') {
            steps {
               sh "mvn clean package"
            }
        }
                    
}
