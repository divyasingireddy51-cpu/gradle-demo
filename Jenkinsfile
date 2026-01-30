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
            // This uses the standalone scanner instead of the Gradle task
            bat "sonar-scanner -Dsonar.projectKey=my-project -Dsonar.sources=app/src/main/java -Dsonar.java.binaries=app/build/classes/java/main"
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

bat "sonar-scanner -Dsonar.projectKey=my-project -Dsonar.sources=app/src/main/java -Dsonar.java.binaries=app/build/classes/java/main"