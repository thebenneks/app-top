pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        // somehow it fails
        sh 'echo "Hello World"'
        sh 'echo "what is in the env: ${env}"'
        sh '''
            echo "Multiline shell steps works too"
            ls -lah
        '''
      }
    }
  } 
}
