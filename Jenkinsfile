pipeline {
  environment {
    TEST_NAME = 'first class test'
  }


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
      steps {
        sh 'ls -lasg'
        sh 'echo "${NODE_NAME}"'
        sh 'lsb_release -a'
        sh 'hostname'
        sh 'mkdir -p data && echo "some data >> data/content"'
        stash includes: 'data', name: 'stashstore'
      }
    }// end stage Build

        // next stage
    stage ('Test'){
      steps {
        unstash 'stashstore'
        sh 'cat data/content'
        sh 'ls -lasg'
        sh 'echo "${NODE_NAME}"'
        sh 'lsb_release -a'
        sh 'hostname'
        sh 'echo ${TEST_NAME}'
      }
    }// end stage Test
  } 
}
