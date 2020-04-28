pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'arduino-cli compile --fqbn arduino:avr:uno Boiler.ino'
      }
    }
    stage('DeployApp') {
            when { tag "SFrelease-*" }
            steps {
                echo 'Deploying release...'
                sh 'cd Scaldofragno && ./gradlew app:buildrelease '
            } */
  }
}
