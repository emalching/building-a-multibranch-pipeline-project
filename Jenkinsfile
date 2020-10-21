pipeline {
  agent any
  stages {
    stage('SonarQube') {
      environment {
        scannerHome = tool 'SonarQubeScanner'
      }

      steps {
        withSonarQubeEnv('sonarqube') {
          sh "${scannerHome}/bin/sonar-scanner"
        }

        timeout(time: 10, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
      }
    }
  }
}
