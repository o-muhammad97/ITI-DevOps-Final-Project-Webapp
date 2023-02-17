pipeline {
    agent any


    stages {
        stage('CI') {
            steps {

                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                sh "cd App"
                sh "docker build . -t ${USERNAME}/webapp:latest"
                sh "docker login -u ${USERNAME} -p ${PASSWORD}"
                sh "docker push ${USERNAME}/webapp:latest"
                sh "cd .."
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
