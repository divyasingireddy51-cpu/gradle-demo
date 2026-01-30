pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pulls the code from your specific repository
                git branch: 'main', url: 'https://github.com/divyasingireddy51-cpu/gradle-demo.git'
            }
        }

        stage('Build & Test') {
            steps {
                // Runs tests and generates the JaCoCo coverage report
                bat 'gradlew.bat clean test'
            }
        }

        stage('Archive Artifact') {
            steps {
                // Compiles the JAR file and stores it in Jenkins
                bat 'gradlew.bat jar'
                archiveArtifacts artifacts: 'app/build/libs/*.jar', fingerprint: true
            }
        }

        stage('SonarQube Analysis') {
            steps {
                // Wraps the gradle command with SonarQube credentials and environment variables
                withSonarQubeEnv('SonarQubeServer') {
                    // Using --no-configuration-cache because Sonar is often incompatible with it
                    // Using --stacktrace to provide detailed error logs if it fails
                    bat 'gradlew.bat sonar -Dsonar.token=squ_92ed2222d7f97e241642b5a7d8b00318233cb00d --no-configuration-cache --stacktrace'
                }
            }
        }
    }
}