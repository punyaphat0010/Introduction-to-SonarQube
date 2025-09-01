pipeline {
    agent any

    tools {
        nodejs "nodejs24.7.0"
        jdk 'jdk17'
    }

    environment {
        JAVA_HOME = "${tool 'jdk17'}"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
        SONARQUBE = credentials('SonarQube')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/punyaphat0010/Introduction-to-SonarQube.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('SonarQube-v25.8.0.112029') {
                    sh 'npx sonar-scanner -Dsonar.projectKey=mywebapp'
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}

