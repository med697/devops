pipeline {
    agent any
    tools {
        maven 'maven3.9.6'
        jdk 'jdk17'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }
    }
}
