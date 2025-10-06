pipeline {
    agent any
    tools {
        maven 'maven3.9.6'
        jdk 'JDK17'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }
    }}
