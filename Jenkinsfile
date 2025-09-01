pipeline {
    agent any

    tools {
        nodejs 'nodejs24.7.0'
    }

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/punyaphat0010/Introduction-to-SonarQube.git'
                sh "npm install"
            }
        }

        // stage('Scan') {
        //     steps {
        //         withSonarQubeEnv(installationName: 'sq1') {
        //             bat "npm install sonar-scanner"
        //             bat 'npx sonar-scanner -X -X -Dsonar.projectKey=mywebapp'
        //         }
        //     }
        // }
    }
}
