pipeline {
    agent { docker { image 'python:3.5.1'} }
    stages {
        stage('Build') {
            steps {
                sh "echo 'Nothing to build here.'"
            }
        }
        stage('Test') {
            steps {
                //pybot samplePyApp/unitTests
                sh "for t in unitTests/*.py; do python \"$t\"; done"
                //sh "python unitTests/app.py"
            }
        }
        stage('Publish') {
            steps {
                sh "echo 'Here a docker image will be created and published'"
            }
        }
    }
}
