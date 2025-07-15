pipeline {
    agent any

    environment {
        PATH = "/opt/flutter/bin:/opt/android-sdk/platform-tools:/opt/android-sdk/cmdline-tools/latest/bin:${env.PATH}"
    }

    stages {
        stage('Trust Flutter Folder') {
            steps {
                sh 'git config --global --add safe.directory /opt/flutter'
            }
        }

        stage('Flutter Doctor') {
            steps {
                sh 'flutter doctor'
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
