pipeline {
    agent any
    tools {
        maven 'maven 3.9.6'
        jdk 'JDK 17'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }
    }}
