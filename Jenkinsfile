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
                // Changed sh to bat for Windows
                bat 'gradlew.bat clean test'
            }
        }
        stage('Archive Artifact') {
            steps {
                // Changed sh to bat for Windows
                bat 'gradlew.bat jar'
                archiveArtifacts artifacts: 'app/build/libs/*.jar', fingerprint: true
            }
        }
    }
}