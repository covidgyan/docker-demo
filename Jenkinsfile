pipeline {
    agent any

    tools {dockerTool "docker_jenkins"}
  
   environment {
        registryCredential = 'dockerhubc'    
    }
    stages {
        stage('Fetch code from Github') {
            steps {
                echo "Fetch job"
                git 'https://github.com/covidgyan/docker-demo.git'
            }
        }
        stage('Build docker image') {
            steps {
                sh 'docker build -t docker_node_demo:latest .'
                sh 'docker tag docker_node_demo myimagehub005/docker_node_demo:latest'
                echo "Build Docker image Succeeded"
            }
        }
        stage('Docker image push') {
            steps {
                echo 'push to dockerhub'       
            }
        }
        
        stage('Run Docker Image') {
            steps {
                sh 'docker run -d -p 3000:3000 myimagehub005/docker_node_demo:latest'
            }
        }
        stage('Deployment in AKS DEV') {
            steps {
                echo 'Deployment in progress'   
                echo 'Deployment Completed'       
            }
        }
         stage('Sonarqube scanning') {
            steps {
                echo 'Scanning in progress'   
                echo 'Scanning Completed'       
            }
        }
         stage('Nexus scanning') {
            steps {
                echo 'Scanning in progress'   
                echo 'Scanning Completed'       
            }
        }
        stage('Whitehat scanning') {
            steps {
                echo 'Scanning in progress'   
                echo 'Scanning Completed'       
            }
        }
        stage('Test in DEV') {
            steps {
                echo 'test in progress'   
                echo 'test Completed'       
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
        stage('Pull Docker image') {
            steps {
                echo 'Successfully  pulled the image'                     
            }
        }
        stage('Deployment in AKS QA') {
            steps {
                echo 'Deployment in progress'   
                echo 'Deployment Completed'       
            }
        }
        stage('Test in QA') {
            steps {
                echo 'test in progress'   
                echo 'test Completed'       
            }
        }
        stage('Approval for ACC deployment') {
            steps {
                echo "Taking approval from QA Manager for ACC Deployment"
                 timeout(time: 7, unit: 'DAYS') {
                     input message: 'Do you want to deploy to ACC?', submitter: 'admin'
                 }
            }
        }
        stage('Pull Docker image') {
            steps {
                echo 'Successfully  pulled the image'                     
            }
        }
        stage('Deployment in AKS ACC') {
            steps {
                echo 'Deployment in progress'   
                echo 'Deployment Completed'       
            }
        }
        stage('Test in ACC') {
            steps {
                echo 'test in progress'   
                echo 'test Completed'       
            }
        }
        stage('Approval for PROD deployment') {
            steps {
                echo "Taking approval from QA Manager for PROD Deployment"
                 timeout(time: 7, unit: 'DAYS') {
                     input message: 'Do you want to deploy to PROD?', submitter: 'admin'
                 }
            }
        }
        stage('Pull Docker image') {
            steps {
                echo 'Successfully  pulled the image'                     
            }
        }
        stage('Deployment in AKS ACC') {
            steps {
                echo 'Deployment in progress'   
                echo 'Deployment Completed'       
            }
        }
        stage('Test in PROD') {
            steps {
                echo 'test in progress'   
                echo 'test Completed'       
            }
        }
    }    
}
