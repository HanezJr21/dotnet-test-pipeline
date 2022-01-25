pipeline {
    agent any
    stages{
        stage('Preparation') {
            steps{
                script{
                    git branch:'main', url: 'https://github.com/HanezJr21/unit-testing.git', credentialsId:'46c0670e-8f6e-4097-934b-ac52ca3e7f16'
                    sh 'pwd'
                    sh 'git submodule update --init --recursive'
                    sh 'ls -ltr'
                }
            }
        }
        stage('Build') {
            steps{
                script{
                    sh 'dotnet test --logger "trx;LogFileName=unit_tests.xml"'
                }
            }
        }
    }
    post {
        always{
            xunit (
                thresholds: [ skipped(failureThreshold: '0'), failed(failureThreshold: '0') ],
                tools: [
                    MSTest(pattern: '**/*.xml')]
            ) 
        }
    }
}
