pipeline {
  agent any
   stages {
    stage("build"){
      steps {
        sh "docker image build --tag $DOCKERID/js_server_jenkins:1.0 ."
      }
    }

    stage("test"){
      steps{
        echo "testing the application..."
      }
    }

    stage("deploy"){
      steps{
        echo "deploying the application..."
      }
    }
   }
}
