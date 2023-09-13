pipeline  {
    agent any
    stages {
        
     stage("checkout") {
         steps {
           git branch: 'master', url: 'https://github.com/AbdelkhalekGuedri/hello-world'
          sh 'whoami'
        }
         
     }
    
      stage("build"){
          steps {
           sh 'mvn package'
          }
        } 
        
        stage("capture"){
          steps {
           archiveArtifacts '**/target/*.war'
          }
        }

    }

  post{
       always {
        emailext body: "${env.JOB_NAME} - Build# ${env.BUILD_NUMBER} -<b> resulat of deployment ${currentBuild.currentResult} </b>", recipientProviders: [developers()], subject: 'Build', to: 'Aabdelkalek' }

    }   
}
    
