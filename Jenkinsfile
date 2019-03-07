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
        sh "docker tag DOCKER_TEST:0.1 kagwima/docker_test:latest"
        sh "docker push kagwima/docker_test:latest"
    }
    stage('Deploy docker'){
        sh "docker run docker_exam:0.1 -p 80:6452"
    }

}