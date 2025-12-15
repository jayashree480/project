pipeline {
  agent any
  tools { jdk 'JDK17'; maven 'Maven3' }
  stages {
    stage('Checkout') { steps { checkout scm } }
    stage('Build') {
      steps {
        script {
          if (isUnix()) { sh 'mvn -B clean package' }
          else { bat 'mvn -B clean package' }
        }
      }
    }
    stage('Archive') { steps { archiveArtifacts artifacts: 'target/*.jar', fingerprint: true } }
  }
}
