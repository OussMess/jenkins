pipeline {
    agent any
    tools {
        maven 'Maven 3.5.2'
        jdk 'jdk1.8.0_151'
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