pipeline {
    agent any

    stages {
        stage('Secret-Masking') {
            steps {
            script{
                MASKED_SECRET = 'I_SHOULD_BE_MASKED'
                wrap([$class: 'MaskPasswordsBuildWrapper', varPasswordPairs: [[password: MASKED_SECRET]]]) { 
                    
                echo 'Retrieve Secret: ' +  MASKED_SECRET
                echo MASKED_SECRET
                sh 'echo Mask that secret without interpolation: $MASKED_SECRET'
                sh 'printenv | grep MASKED_SECRET'

             }
        } 
      }
    }
  }
}
