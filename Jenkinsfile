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
 	sh "docker login -u='uanozi200' -p='Childofgod2100'"
        sh "docker image push uanozi200/js_server_cw2:1.0"
 	sh "chmod 777 kubectl.sh"
 	sh "./kubectl.sh"
	sh "chmod 777 minikube.sh"
 	sh "./minikube.sh"
 	sh "chmod 777 k8s.sh"
  	sh "./k8s.sh"
      }
    }
   }
}
