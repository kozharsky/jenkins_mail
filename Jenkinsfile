pipeline {
    agent any
    stages {
          stage(''){
              steps{
                env.BUILD_STATUS = 'FAILED'
              }
          }
          stage('Echo') {
             steps {
                 echo "Hello"
             }
          }
         stage('Send') {
            steps {
               emailext (
               to: '$ghprbActualCommitAuthorEmail',
               subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - ' + "${env.BUILD_STATUS}",
               body: 'Project: $PROJECT_NAME<br/>Build # $BUILD_NUMBER<br/>Build status: ' + "${env.BUILD_STATUS}" + '<br/>View job results: $BUILD_URL<br/>Console output:<br/>${BUILD_URL}consoleFull'
               )
            }
         }
     }
 }
