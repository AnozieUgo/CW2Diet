CODE_CHANGES = getGitChanges()
pipeline {
  agent any
   stages {
    stage("build"){
      when {
	expression {
	  CODE_CHANGES == true
        }
      }
      steps {
        sh "docker image build --tag uanozi200/js_server_jenkins:1.0 ."
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
