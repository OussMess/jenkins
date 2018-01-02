pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'java8'
    }
    stages {
        
        stage ('Build') {
            steps {
            bat 'mvn install'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
            steps {
            bat 'mvn cobertura:cobertura'
            }
            post {
                success {
                    cobertura 'target/site/cobertura/coverage.xml'
                }
            }
        }
    }
}