pipeline {
    stages{
        stage('Preparation') {
            git 'https://github.com/HanezJr21/unit-testing-using-dotnet-test.git'
        }
        stage('Build') {
            sh 'dotnet test --logger "trx;LogFileName=unit_tests.xml"'
        }
        stage('Results') {
            mstest testResultsFile:"**/*.trx", keepLongStdio: true
        }
    }
}