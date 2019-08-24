pipeline {
  environment {
    TEST_NAME = 'first class test'
    SYSUSER = credentials('sysid')
  }


  agent any
  stages {
    stage('Checkout') {
      steps {
        // somehow it fails
        sh 'echo "next is output of sysid"'
        sh 'echo "systemuser ${SYSUSER_USR}:${SYSUSER_PSW}"'
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
      agent {
        docker {
          image 'maven'
        }
      }
      steps {
        sh 'ls -lasg'
        sh 'echo "${NODE_NAME}"'
        sh 'mvn clean install -DskipTests'
        sh 'mkdir -p bin'
        sh 'cp target/*.jar bin/'
        sh 'ls -aslg  bin/'
        stash includes: 'bin/*', name: 'stashstore'
      }
    }// end stage Build

        // next stage
    stage ('Test'){
      steps {
        unstash 'stashstore'
        sh 'ls -aslg bin/'
        sh 'ls -lasg'
        sh 'echo "${NODE_NAME}"'
        sh 'hostname'
        sh 'echo ${TEST_NAME}'
      }
    }// end stage Test
  } 
}
