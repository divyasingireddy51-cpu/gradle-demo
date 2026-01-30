pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/divyasingireddy51-cpu/gradle-demo.git'
            }
        }
        stage('Build & Test') {
            steps {
                bat 'gradlew.bat clean test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                    withSonarQubeEnv('SonarQubeServer') {
                    bat 'gradlew.bat sonar'
                }
            }
        }
        stage('Archive Artifact') {
            steps {
                bat 'gradlew.bat jar'
                archiveArtifacts artifacts: 'app/build/libs/*.jar', fingerprint: true
            }
        }
    }
}