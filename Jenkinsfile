pipeline {
  agent none

  stages {
    stage('Deliver Docker images') {
      agent {
        docker {
          image 'docker:19.03.12-dind'
          args '-e PROGRESS_NO_TRUNC=1 -e DOCKER_HOST=$DOCKER_HOST -e DOCKER_BUILDKIT=1'
        }
      }
      steps {
        script {
          def dockerImage = docker.build('tanandy/openpaas-front', '--pull --no-cache .')
          docker.withRegistry('', 'dockerHub') {
            //dockerImage.push('branch-main')
          }
        }
      }
    }
  }
}
