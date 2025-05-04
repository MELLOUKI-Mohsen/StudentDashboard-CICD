pipeline {
    agent any

    tools {
        maven 'Maven 3.8.5'
    }

    environment {
        SONARQUBE_SCANNER_HOME = tool 'SonarQube Scanner'
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/MELLOUKI-Mohsen/StudentDashboard-CICD.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t student-dashboard .'
            }
        }
    }
}
