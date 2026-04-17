pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Nabeelanaushadkhan/MyMavenToGradle'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'build/libs/*.jar'
            }
        }
    }
}
