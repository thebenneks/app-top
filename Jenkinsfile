pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        // somehow it fails
        sh 'echo "Hello World"'
        sh 'echo "what is in the env: ${GIT_BRANCH}  and ${GIT_COMMIT}"'
        sh '''
            echo "Multiline shell steps works too"
            ls -lah
        '''
      }
    }
  } 
}
