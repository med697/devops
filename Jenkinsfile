pipeline {
    agent any
    tools {
        maven 'Maven'
        jdk 'Java17'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }
    }}
