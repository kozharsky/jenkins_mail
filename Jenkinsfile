pipeline {
    agent any
    stages {
           stage('FAILED'){
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
                sh """
                    pm_version_number=testValue
                    s3_bucket_name=dimak-test

                    dirName=IP_JOP_PRR_${pm_version_number}_ENU_linux
                    ipFileName=${dirName}.tar.gz
                    OldipFileName=${dirName}_OLD.tar.gz

                    aws s3 ls s3://"$s3_bucket_name"/PM_IP/"$OldipFileName"

                    if [ $? -eq 0 ]; then
                        aws s3 cp s3://"$s3_bucket_name"/PM_IP/"$ipFileName" s3://"$s3_bucket_name"/PM_IP/"$OldipFileName"
                    fi

                    aws s3 cp $OldipFileName  s3://"$s3_bucket_name"/PM_IP/"$ipFileName"
				    """
               )
            }
         }
     }
 }
