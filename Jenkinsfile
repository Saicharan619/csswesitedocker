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
            sh "docker build -t shivaanna . "
    }
        }
            stage("container"){
               steps{
                 sh "docker run -itd --name saitejaameda shivaanna"
}
            }
        }
    }

