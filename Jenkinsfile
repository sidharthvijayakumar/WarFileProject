node{
  stage('SCM Checout'){
   
  git 'https://github.com/sidharthvijayakumar/WarFileProject'
  }
  stage('Build'){
     def mvnHome = tool name: 'Maven', type: 'maven'
    sh "${mvnHome}/bin/mvn clean package"
  }
  stage("publish to s3") {
      
  s3Upload(file:'/var/lib/jenkins/workspace/WarPipeline/target/sparkjava-hello-world-1.0.war', bucket:'s3artifactsforjenkins', path:'target')
    
  } 
  stage("deploy"){  
  sshagent(['deploy_Proj']) {
     sh "scp -o StrictHostKeyChecking=no target/sparkjava-hello-world-1.0.war ec2-user@3.23.89.23:/root/tom/webapps"
      
      }
  }

   stage("E-mail notification"){
    mail bcc: '', body: 'Your build has been done please check the results.', cc: '', from: '', replyTo: '', subject: 'Jenkins Project-WarPipeline', to: 'sidharthvijayakumar7@gmail.com' 
  }
 
}
