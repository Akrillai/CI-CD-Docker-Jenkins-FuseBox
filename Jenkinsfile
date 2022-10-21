pipeline {
    agent any
	
	  tools
    {
       maven "m3"
    }
 stages {
      stage('git clone') {
            steps {
                git 'https://github.com/Akrillai/boxfuse-sample-java-war-hello.git'
                sh "mvn clean package"
            }

        }
	 stage('Execute Maven') {
           steps {
             
                sh 'cd boxfuse-sample-java-war-hello && mvn package'
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t mywebapp1420:latest .' 
               
          }
        }
     
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh "docker -H ssh://root@172.31.3.13 run -d -p 8008:8080 mywebapp1420"
 
            }
        }
    }
 }
