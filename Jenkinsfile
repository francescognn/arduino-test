node {
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/francescognn/arduino-test.git'

   }
   stage('Build') {
        // Run the maven build
      setGitHubPullRequestStatus context: 'Arduino-Build', message: 'Compiling ...', state: 'PENDING'
      sh 'arduino-cli compile --fqbn arduino:avr:uno Boiler.ino'
      
   }
   stage('Test') {
      sh 'echo Test'
   }
}
