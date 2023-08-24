pipeline {
agent any
stages {
  
stage ("List Files") {
  steps {
sh 'pwd'
sh 'ls -ltr'
  }
}
  
  stage ("Build Nodejs Image") {
    steps {
      sh 'sudo docker build -t httpd02 .'
      sh 'sudo docker ps'
    }
  }
  
  stage ("Delivery of Image to Docker Hub") {
    steps {
      sh 'sudo docker image tag httpd02 devopsJenkins/httpd02:1.0'
      sh 'sudo docker push devopsJenkins/nodejs:1.0'
    }
  }
  
    stage ("Deployment to Kubernetes") {
    steps {
      sh 'chmod 400 <pemfile>'
      sh 'ls -ltr'
      sh 'scp -i <pemfile> -o StrictHostKeyChecking=no rep01.yml ec2-user@<IP>:/home/ec2-user/'
      sh 'ssh -i <pemfile> -o StrictHostKeyChecking=no ec2-user@<IP> "kubectl delete -f rep01.yml"'
      sh 'ssh -i <pemfile> -o StrictHostKeyChecking=no ec2-user@<IP> "kubectl create -f rep01.yml"'
    }
  }
  
 
}
}
