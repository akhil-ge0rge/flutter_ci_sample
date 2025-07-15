pipeline {
    agent any

    environment {
        FLUTTER_HOME = "/usr/local/flutter" // <-- Change this if Flutter is in a different path
        PATH = "${FLUTTER_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/akhil-ge0rge/flutter_ci_sample.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'flutter pub get'
            }
        }

        stage('Build APK') {
            steps {
                sh 'flutter build apk --release'
            }
        }

        stage('Archive APK') {
            steps {
                archiveArtifacts artifacts: 'build/app/outputs/flutter-apk/app-release.apk', fingerprint: true
            }
        }
    }
}