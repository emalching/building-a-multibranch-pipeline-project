pipeline {
  agent any
  stages {
    stage('SonarQube') {
      environment {
        scannerHome = tool 'SonarQubeScanner'
      }

      steps {
        withSonarQubeEnv('SonarQube') {
          sh "${scannerHome}/bin/sonar-scanner"
        }

        timeout(time: 10, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
      }
    }
  }
}
