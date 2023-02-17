pipeline {
    agent any


    stages {
        stage('CI') {
            steps {

                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                sh """
                 cd App
                 sudo docker build . -t ${USERNAME}/webapp:latest
                 docker login -u ${USERNAME} -p ${PASSWORD}
                 docker push ${USERNAME}/webapp:latest
                 cd ..
                 """
                }
                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }


        }
        stage('CD'){
            steps{
                  sh """
                  kubectl apply -f Deployment
                  """

            }

        }
    }
}
