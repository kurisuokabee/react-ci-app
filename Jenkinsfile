
pipeline {
    agent any

    tools {
        nodejs 'NodeJS-22'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Test') {
            steps {
                sh 'npm install'
                sh 'npm test -- --run'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Archive Artifact') {
            steps {
                sh "tar -czf react-app-${BUILD_NUMBER}.tar.gz dist Dockerfile"

                archiveArtifacts artifacts: "react-app-${BUILD_NUMBER}.tar.gz",
                                 fingerprint: true
            }
        }
    }
}
