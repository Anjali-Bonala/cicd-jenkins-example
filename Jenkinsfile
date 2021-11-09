pipeline {

    agent any
       tools {
          maven 'maven'
       }
 stages {
       stage ('Build') {
            steps {
               
                    sh 'mvn clean install'
            }
        }

       stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                    sh '/Users/bonala.anjali/Downloads/cf-cli-installer_6.53.0_winx64 (1)/cf login -a http://api.run.pivotal.io -u $USERNAME -p $PASSWORD'
                    sh '/Users/bonala.anjali/Downloads/cf-cli-installer_6.53.0_winx64 (1)/cf push'
                }
            }

        }

    }

}
