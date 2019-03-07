node {

    stage('Clone the repository')
    {
        checkout scm
    }
    stage('Build a docker image') {

        sh "docker build -t docker_exam:0.1 ."	
    }
    stage('Push image to dockerhub') {
        sh "docker login  -u 'kagwima' -p 'K@d506112007' "	
        sh "docker tag docker_exam:0.1 kagwima/docker_exam:latest"
        sh "docker push kagwima/docker_exam:latest"
    }
    stage('Deploy'){
        sh "docker run -d -p 4411:6452/tcp docker_exam:0.1"
       
         }

}
