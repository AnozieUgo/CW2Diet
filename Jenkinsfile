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
 	sh "sudo apt-get update"
 	sh "sudo apt-get install -y apt-transport-https"
 	sh "curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -"
 	sh "echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list"
 	sh "sudo apt-get update"
 	sh "sudo apt-get install -y kubectl"
	sh "curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64"
 	sh "chmod +x minikube"
 	sh "sudo mv minikube /usr/local/bin/"
 	sh "kubectl create deployment kubernetes-bootcamp --image=https://hub.docker.com/repository/docker/uanozi200/js_server_cw2"
      }
    }
   }
}
