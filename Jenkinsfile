pipeline{
    agent any 
    stages{
        stage("Hello"){
            steps{
                git branch: 'main', url: 'https://github.com/ameda71/csswesite.git'
            } 
        }
    
stage("Completed"){
      steps{
          echo "Completed"
    }
}
        stage("Build"){
          steps {
            sh "sudo docker build -t prabas . "
    }
        }
            stage("container"){
               steps{
                 sh "sudo docker run -d -p 55:80 --name salaar prabas"
}
            }
        }
    }

