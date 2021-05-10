pipeline {
    agent any
    //{
   //     docker {
   //         image 'node:lts-buster-slim'
   //         args '-p 3000:3000'
  //      }
 //  }
 //   tools {nodejs "nodejs1"}
    tools {dockerTool "docker_jenkins"}
   // tool name: 'docker_jenkins', type: 'dockerTool'
   // environment {
   //     CI = 'true'
   // }
   environment {
        //once you sign up for Docker hub, use that user_id here
      //  registry = "your_docker_user_id/mypythonapp"
        //- update your credentials ID after creating credentials for connecting to Docker Hub
        registryCredential = 'dockerhubc'
     //   dockerImage = ''
    }
    stages {
        stage('fetch') {
            steps {
                echo "Fetch job"
                git 'https://github.com/covidgyan/docker-demo.git'
              //  sh 'npm install'
            //    sh 'npm start'
            }
        }
        stage('docker build') {
            steps {
                sh 'docker build -t docker_node_demo:latest .'
               // sh 'docker build -t nginxtest:latest .' 
                  sh 'docker tag docker_node_demo myimagehub005/docker_node_demo:latest'
            }
        }
        stage('Docker image push') {
            steps {
           //     script {
            //        docker.withRegistry( '', registryCredential ) {
            //        dockerImage.push()
            //    }
           //  }
             //   withCredentials([string(credentialsId: 'dockerhubpwdstring', variable: 'DockerhubPwd')]) {
             //   sh 'docker login -u myimagehub005 -p $DockerhubPwd'
            //}
          //withDockerRegistry(credentialsId: 'dockerhubc', url: 'https://hub.docker.com/repository/docker/myimagehub005/docker_node_demo/') {
           // sh 'docker push myimagehub005/docker_node_demo:2.0.0'
          //      }
            //    sh 'docker push myimagehub005/docker_node_demo:2.0.0'
          //      withDockerRegistry(credentialsId: 'dockerhubc', url: '') {
          //      sh 'docker push myimagehub005/docker_node_demo:2.0.0'
            echo 'puch to dockerhub'
          //      }
       //    withDockerRegistry([ credentialsId: "dockerhubc", url: "" ]) {
        //         sh  'docker push myimagehub005/docker_node_demo:latest'
        //  sh  'docker push nikhilnidhi/nginxtest:$BUILD_NUMBER' 
      //  }
            }
        }
        
        stage('Docker run') {
            steps {
                sh 'docker run -d -p 3000:3000 myimagehub005/docker_node_demo:latest'
            }
        }
         stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
         }
        stage('Approval for QA deployment') {
            steps {
                echo "Taking approval from DEV Manager for QA Deployment"
                 timeout(time: 7, unit: 'DAYS') {
                     input message: 'Do you want to deploy to QA?', submitter: 'admin'
                 }
            }
        }
    }
       
      //  stage('Deliver') {
       //     steps {
       //         sh './jenkins/scripts/deliver.sh'
       //         input message: 'Finished using the web site? (Click "Proceed" to continue)'
       //         sh './jenkins/scripts/kill.sh'
      //      }
      //  }
    
}
