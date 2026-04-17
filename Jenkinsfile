pipeline {
    agent any

    tools {
        // If Gradle is installed in Jenkins
        gradle 'Gradle-8'
        jdk 'JDK17'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Nabeelanaushadkhan/MyMavenToGradle.git'
            }
        }

        stage('Grant Permission') {
            steps {
                sh 'chmod +x gradlew'
            }
        }

        stage('Clean Build') {
            steps {
                sh './gradlew clean'
            }
        }

        stage('Compile') {
            steps {
                sh './gradlew build -x test'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Build Jar') {
            steps {
                sh './gradlew bootJar || ./gradlew jar'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build Successful 🎉'
        }
        failure {
            echo 'Build Failed ❌'
        }
    }
}
