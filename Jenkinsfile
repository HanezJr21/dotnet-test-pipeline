pipeline {
    agent any
    stages{
        stage('Preparation') {
            steps{
                script{
                    git branch:'main', url: 'https://github.com/HanezJr21/unit-testing-using-dotnet-test.git'
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
