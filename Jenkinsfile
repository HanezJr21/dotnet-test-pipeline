node {
    stage('Preparation') { // for display purposes
        git branch:'main', url: 'https://github.com/HanezJr21/unit-testing-using-dotnet-test.git'
        sh 'ls -l'
    }
    stage('Build') {
        sh 'dotnet test --logger "trx;LogFileName=unit_tests.trx"'
    }
    stage('Results') {
        mstest testResultsFile:"**/*.trx", keepLongStdio: true
    }
}
