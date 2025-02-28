
pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Srilakshmisumathi/Test-Jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'chmod +x tesetup.sh && ./tesetup.sh'  // Modify as needed
            }
        }

        stage('Run Tests') {
            steps {
                sh 'chmod +x test.sh && ./test.sh'  // Running test script
            }
        }

        stage('Archive Test Results') {
            steps {
                archiveArtifacts artifacts: '**/test-results/*.xml', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Tests Passed Successfully!'
        }
        failure {
            echo '❌ Tests Failed!'
        }
    }
}

