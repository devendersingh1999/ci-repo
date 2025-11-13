pipeline{
    agent any

    environment{
        GIT_CRED = 'ci-app-token'
        GIT_URL = 'https://github.com/devendersingh1999/application-repo.git'
    }

    stages{
        stage('checkout'){
          steps{
              git(
                url: "${GIT_URL}",
                branch: "app-new", //branch app-new 
                credentialsId: "${GIT_CRED}"
            )
          }
         }

        stage('Build'){
            steps{
                sh''' 
                chmod 777 app-new.sh
                ./app-new.sh
                '''
            }
        }
        stage('after Build'){
            steps{
                echo "The build is completed"
            }
        }
    }

    post{
        success{
            echo "pipeline succeeded"
        }
        failure{
            echo "pipeline failed"
        }
    }
}