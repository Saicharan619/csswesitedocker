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
            sh "docker build -t rajamannar . "
    }
        }
        stage("login"){
          steps {
            sh "docker loginc-u saicharan12121 "
            sh "itachi@619"
    }
        }
        stage("tag"){
          steps {
            sh "docker tag rajamannar saicharan12121/rajamannar:latest"
    }
        }
        stage("push"){
          steps {
            sh "docker push saicharan12121/rajamannar:latest"
    }
        }
            stage("container"){
               steps{
                 sh "docker run -d -p 515:80 --name websalaar rajamannar"
}
            }
        }
    }

