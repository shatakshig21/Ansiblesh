pipeline {
    agent any  // Use any available agent
    

    tools {
        maven 'Maven'  // Ensure this matches the name configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/shatakshig21/Ansiblesh.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'  // Run Maven build
            }
        }

     stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint:true
            }
        }
        stage('Deploy') {
            steps {
 
               sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
            }
        }

                  
    }

   }
   
