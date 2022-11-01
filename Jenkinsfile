pipeline{
    agent none
    stages{
        stage('gitclone'){
            agent any
            steps{
                git credentialsId: 'bc010765-2802-482d-8502-5f629f70228a', url: 'https://github.com/sreyaku/JavaApplication-JenkinsCICD.git'
            }
        }
        
        
        stage('compile'){
            agent any
            steps{
                bat 'mvn compile'
            }
        }
        
        stage('test'){
            agent any
            steps{
               bat 'mvn test'
            }
        }
        stage('package'){
            agent any
            steps{
                bat 'mvn package'
            }
        }
    
        stage(deploy){
            agent any 
            steps{
   
              bat '''
                docker container stop yourcontainer
            docker container rm yourcontainer
            docker image build -t testimage:1.0 .
            //docker run  --rm -d -p 80:8082 testimage:1.0
             docker run -d -p 80:8082 --name yourcontainer testimage:1.0
            '''
        }
    }    
    }
    }
