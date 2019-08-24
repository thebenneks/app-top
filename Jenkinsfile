pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        // somehow it fails
        sh 'echo "Hello World"'
        sh '''
            echo "Multiline shell steps works too"
            ls -lah
        '''
    }
  }
}
