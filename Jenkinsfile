pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }}
        stage('Build') {
            steps {
                bat 'python3 -m py_compile app.py'
                sleep time: 15, unit: 'SECONDS'
                milestone ordinal: 1
            }}
        stage('Send Notification') {
            steps {          
                echo "Notification"
                echo "To: manikandanrenu3@gmail.com"
                echo "Subject: Build ${env.JOB_NAME} #${env.BUILD_NUMBER}"
                echo "Body: Build URL: ${env.BUILD_URL}"
            }}}}