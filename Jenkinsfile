pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Nabeelanaushadkhan/MyMavenToGradle'
            }
        }

       stage('Build') {
    steps {
        dir('MyMavenToGradle/MyMavenApp') {
            sh './gradlew clean build'
        }
    }
}

        stage('Test') {
    steps {
        dir('MyMavenToGradle/MyMavenApp') {
            sh './gradlew test'
        }
    }
}

        stage('Archive') {
    steps {
        archiveArtifacts artifacts: 'MyMavenToGradle/MyMavenApp/build/libs/*.jar'
    }
}
}
}
