pipeline {
    agent { docker { image 'python:3.5.1'} }
    stages {
        stage('Checkout') {
            steps {
                git branch: "master",
                    url: 'https://github.com/ValeriaRe/PySample.git'
            }
        }
        stage('Build') {
            steps {
                sh "echo 'Nothing to build here.'"
                sh "cat ${WORKSPACE}/deployment.yaml"
            }
        }
        stage('Test') {
            steps {
                //pybot unitTests
                //sh "for t in unitTests/*.py; do python \"$t\"; done"
                sh "python unitTests/app.py"
            }
        }
        stage('Publish') {
            steps {
                sh "echo 'Publishing to contaioner registry...'"
                withKubeConfig([credentialsId: '2d731f46-6853-49a6-9ce5-f6238dc25e48', serverUrl: 'https://10.40.235.147:6443']) {
                    sh 'kubectl create -f ${WORKSPACE}/deployment.yaml --namespace=valeria-mgmt'
                }
                sh "echo 'Successfully published!'"
            }
        }
    }
}
