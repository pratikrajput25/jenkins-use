pipeline {
    agent any

    tools {
        // Ensure this name matches what you set in Jenkins Global Tool Configuration
        jdk 'jdk25'
        maven 'maven3'
    }

    stages {
        stage('Environment Check') {
            steps {
                // 'bat' is used for Windows Command Prompt
                bat 'java -version'
                bat 'mvn -version'
            }
        }

        stage('Compile') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package -DskipTests'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
        }
    }
}
