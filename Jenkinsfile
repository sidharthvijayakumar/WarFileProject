node{
  stage('SCM Checout'){
   
  git 'https://github.com/sidharthvijayakumar/WarFileProject'
  }
  stage('Build'){
     def mvnHome = tool name: 'Maven', type: 'maven'
    sh "${mvnHome}/bin/mvn clean package"
  }
  stage("publish to s3") {
      
     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'sparkjava-hello-world-1.0.war', bucket:'s3-artifactsforjenkins', path:'*/var/lib/jenkins/workspace/WarPipeline/target/sparkjava-hello-world-1.0.war')
    
  } 
   stage("E-mail notification"){
    mail bcc: '', body: 'Your build has been done please check the results.', cc: '', from: '', replyTo: '', subject: 'Jenkins Project-WarPipeline', to: 'sidharthvijayakumar7@gmail.com' 
  }
 
}
