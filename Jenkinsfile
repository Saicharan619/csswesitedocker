pipeline{
    agent any 
    stages{
        stage("Hello"){
            steps{
                git branch: 'main', url: 'https://github.com/Saicharan619/csswesitedocker.git'
            } 
        }
    
stage("Completed"){
      steps{
          echo "Completed"
    }
}
        stage("Build"){
          steps {
            sh "docker build -t rajamannar . "
    }
        }
            stage("container"){
               steps{
                 sh "docker run -d -p 55:80 --name salaar rajamannar"
}
            }
        }
    }

