pipeline {
    agent none
    stages {
        stage('Login'){
            agent{
                node{
                    label 'master'
                }
            }
            steps {
                echo 'docker login'
                sh 'docker login -u devopsutec -p eYUZB+kRWGt19mj8Lj1RpbmSKnwdtw33 devopsutec.azurecr.io'
            }
        }

        stage('Build_imagenes') {
            agent{
                node{
                    label 'master'
                }
            }
        steps{
            dir('worker'){
                sh 'docker build -t devopsutec.azurecr.io/innova2-worker-1.0:${BUILD_NUMBER} .' 
             }
                dir('vote'){
                sh 'docker build -t devopsutec.azurecr.io/innova2-vote-1.0:${BUILD_NUMBER} .' 
             }
                dir('result'){
                sh 'docker build -t devopsutec.azurecr.io/innova2-result-1.0:${BUILD_NUMBER} .' 
             }
        
            }
        }             

        stage('Push_imagenes') {
            agent {
                node{
                    label 'master'
                }
            }
            steps {      
                echo 'Push imagenes'  
                sh 'docker push devopsutec.azurecr.io/innova2-worker-1.0:${BUILD_NUMBER}' 
                sh 'docker push devopsutec.azurecr.io/innova2-vote-1.0:${BUILD_NUMBER}' 
                sh 'docker push devopsutec.azurecr.io/innova2-result-1.0:${BUILD_NUMBER}' 
            }
        }

 
        stage('Docker_compose') {
            agent {
                node {
                    label 'utec'
                }
            }
            steps {
                echo 'docker compose'
                sh 'docker-compose up -d'
<<<<<<< HEAD
<<<<<<< HEAD
            }
        }

    }
=======
=======
>>>>>>> origin
             }
         }
 
      }
<<<<<<< HEAD
  }
>>>>>>> 1c2e00b... jenkins 3
=======
>>>>>>> origin
}