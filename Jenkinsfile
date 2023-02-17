pipeline {
    agent any


    stages {
        stage('CI') {
             steps {

                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                sh "docker build . -f Dockerfile -t $JOB_NAME:v1.$BUILD_ID"
                sh "docker tag $JOB_NAME:v1.$BUILD_ID ${USERNAME}/$JOB_NAME:v1.$BUILD_ID"
                sh "docker tag $JOB_NAME:v1.$BUILD_ID ${USERNAME}/$JOB_NAME:latest"
                sh "docker login -u ${USERNAME} -p ${PASSWORD}"
                sh "docker push ${USERNAME}/$JOB_NAME:v1.$BUILD_ID"
                sh "docker push ${USERNAME}/$JOB_NAME:latest"
}              
}
}
        stage('CD'){
            steps{
                  sh """
                  kubectl apply -n jenkins -f deployment.yaml
                  kubectl apply -n jenkins -f service.yaml
                  """

            }

        }
    }
}
