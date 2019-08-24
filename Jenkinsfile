pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        // somehow it fails
        sh 'echo "Hello World"'
        sh 'echo "what is in the env: ${BRANCH_NAME}  and ${BUILD_NUMBER} plus ${CHANGE_ID}"'
        sh '''
            echo "Multiline shell steps works too"
            ls -lah
        '''
      }
    }// end stage Checkout

    // next stage
    stage ('Build'){
      sh 'ls -lasg'
      sh 'echo "${NODE_NAME}"'
    }// end stage Build
  } 
}
