pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'arduino-cli compile --fqbn arduino:avr:uno Boiler.ino'
      }
    }

    stage('DeployApp') {
      when {
        tag pattern: 'SFrelease-*', comparator: 'REGEXP'
      }
      steps {
        echo 'Deploying release...'
        sh 'cd ScaldoFragno && export ANDROID_SDK_ROOT="/home/ictadmin/Android/Sdk" && ./gradlew app:build'
        archiveArtifacts(artifacts: 'ScaldoFragno/app/build/outputs/apk/release/app-release-unsigned.apk', onlyIfSuccessful: true)
      }
    }

  }
}