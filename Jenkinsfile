node{
  stage('SCM Checout'){
   
  git 'https://github.com/sidharthvijayakumar/WarFileProject'
  }
  stage('Build'){
     def mvnHome = tool name: 'Maven', type: 'maven'
    sh "${mvnHome}/bin/mvn clean package"
  }
   stage("E-mail notification"){
    mail bcc: '', body: 'Your build has been done please check the results.', cc: '', from: '', replyTo: '', subject: 'Jenkins Project-WarPipeline', to: 'sidharthvijayakumar7@gmail.com' 
  }
 
}
