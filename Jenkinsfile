pipeline {
    agent any


    stages {
        stage('CI') {
             steps {
            withCredentials([usernamePassword(credentialsId: 'git', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                git 'https://github.com/o-muhammad97/ITI-DevOps-Final-Project-Webapp.git'
}
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
                  kubectl apply -f deployment.yaml
                  kubectl apply -f service.yaml
                  """

            }

        }
    }
}
