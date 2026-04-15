pipeline {
    agent any  // Use any available agent

    tools {
        gradle 'Gradle'  // Ensure this matches the name configured in Jenkins
        jdk 'JDK'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/MadhuryaAK/MyGradleApp.git'
            }
        }
        stage('Build') {
            steps {
                sh 'chmod +x gradlew && ./gradlew build'  // Run Gradle build
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'  // Run unit tests
            }
        } 
        stage('Run Application') {
            steps {
                // Start the JAR application
                sh './gradlew run &'
            }
        }
    }
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
