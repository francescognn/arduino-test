pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'arduino-cli compile --fqbn arduino:avr:uno Boiler.ino'
      }
    }
    stage('DeployApp') {
            when { tag pattern: 'SFrelease-*', comparator: "REGEXP" }
            steps {
                echo 'Deploying release...'
                sh 'cd ScaldoFragno && ./gradlew app:buildrelease '
            }
    }
  }
}
