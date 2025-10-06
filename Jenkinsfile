pipeline {
    agent any

    tools {
        maven 'maven3.9.6'   // must match Maven name in Global Tool Config
        jdk 'JDK17'          // must match JDK name in Global Tool Config
    }

    // Optional: if you don’t have GitHub webhook, uncomment this line
    // triggers { pollSCM('H/5 * * * *') }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                // Compile and package with tests
                sh 'mvn -B clean package'
            }
        }

        stage('Unit Tests (publish)') {
            steps {
                // Publish test results to Jenkins
                junit 'target/surefire-reports/*.xml'
            }
        }

        stage('Archive Artifact') {
            steps {
                // Archive the generated jar file(s) so you can download from Jenkins
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            // Clean workspace and re-publish tests even if failure
            junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'
            cleanWs()   // requires Workspace Cleanup plugin
        }
        success {
            echo "✅ BUILD SUCCESSFUL"
        }
        failure {
            echo "❌ BUILD FAILED - check Console Output"
        }
    }
}
