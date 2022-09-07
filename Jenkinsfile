pipeline {
    agent any

    stages {
        stage('Secret-Masking') {
            steps {
            script{
                MASKED_SECRET = 'I_SHOULD_BE_MASKED'
                wrap([$class: 'MaskPasswordsBuildWrapper', 
                     varPasswordPairs: [[password: MASKED_SECRET]]]) { 
                  withEnv(["SECRET=${MASKED_SECRET}"]){
                  echo 'Whoops interpolated secret leaked in Blue Ocean: ' + SECRET
                  sh 'echo Mask that secret without interpolation: $SECRET'
                  sh 'printenv | grep SECRET'
            }
          }
        }
      }
    }
  }
}
