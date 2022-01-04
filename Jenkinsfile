pipeline {
    stages{
        stage('Preparation') {
            git 'https://github.com/HanezJr21/ExpressJS.git'
        }
        stage('Build') {
            sh "npm install"
        }
        stage('Results') {
            archiveArtifacts artifacts: '**', excludes: 'test*/'
        }
    }
}