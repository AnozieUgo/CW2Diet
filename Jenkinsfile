pipeline {
  agent any
   stages {
    stage("build"){
      steps {
 	sh "docker container stop js_server_cw2"
 	sh "docker container rm js_server_cw2"
 	echo "Building docker image for js_server_cw2"
        sh "docker image build --tag uanozi200/js_server_cw2:1.0 ."
      }
    }

    stage("test"){
      steps{
        echo "testing the docker image"
 	sh "docker container run --detach --publish 80:80 --name js_server_cw2 uanozi200/js_server_cw2:1.0"
      }
    }

    stage("deploy"){
      steps{
 	sh "docker login --username=uanozi200 --password-stdin <<<'Childofgod2100'"
        sh "docker image push uanozi200/js_server_cw2:1.0"
      }
    }
   }
}
