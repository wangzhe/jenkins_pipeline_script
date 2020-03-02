 def my_attachments = [
  [
    text: "Hi PHP developers, Pipeline: ${env.JOB_NAME} \n Build: #${env.BUILD_NUMBER} failed :red_circle: fix it asap before something happened! :see_no_evil: \n URL: ${env.JOB_URL}",
    fallback: 'Hey, Santa Claus seems to be mad at you. haha',
    color: '#ff0000'
  ]
]
         
 pipeline {  
     agent any  
     stages {  
         stage('Test') {  
             steps {  
                 sh 'echo "Fail!"; exit 1'  
             }  
         }  
     }  
     post {  
         always {  
             echo 'This will always run' 
         }  
         success {  
             echo 'This will run only if successful'  
         }  
         failure {  
             echo 'This will run only if the run was marked as failed'
             slackSend(channel: '#jenkins-failure', attachments: my_attachments)  
         }  
         unstable {  
             echo 'This will run only if the run was marked as unstable'  
         }  
         changed {  
             echo 'This will run only if the state of the Pipeline has changed'  
             echo 'For example, if the Pipeline was previously failing but is now successful'  
         }  
     }  
 }
