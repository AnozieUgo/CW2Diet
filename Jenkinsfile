pipeline {
  agent any
   stages {
    stage("build"){
      steps {
 	echo "Building docker image for js_server_jenkins"
        sh "docker image build --tag uanozi200/js_server_jenkins:1.0 ."
      }
    }

    stage("test"){
      steps{
        echo "testing the docker image"
 	sh "docker container run --detach --publish 80:80 --name js_server_jenkins uanozi200/js_server_jenkins:1.0"
      }
    }

    stage("deploy"){
      steps{
        echo "deploying the application..."
      }
    }
   }
}
