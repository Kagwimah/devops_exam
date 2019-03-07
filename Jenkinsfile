node {

    stage('Clone the repository')
    {
        checkout scm
    }
    stage('Build a docker image') {

        sh "docker build -t docker_exam:1.0 ."	
    }
    stage('Push image to dockerhub') {
        sh "docker login  -u 'kagwima' -p 'K@d506112007' "	
        sh "docker tag docker_exam:0.1 kagwima/docker_exam:1.0"
        sh "docker push kagwima/docker_exam:1.0"
    }
  stage('Run') {
    steps {
        echo "Run docker image"
        script {
            pipelineContext.dockerContainer = pipelineContext.dockerImage.run()
        }
    }
}

}
