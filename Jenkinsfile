pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  
  
 stages {
   
   stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }
    
   stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }
    
   stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@18.215.160.30:/prod/apache-tomcat-8.5.56/webapps/webapp.war'
              }      
           }
    }
    
    
    
    
    
    
  }
}


