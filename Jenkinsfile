node{
  stage('SCM Checout'){
   
  git 'https://github.com/sidharthvijayakumar/WarFileProject'
  }
  stage('Build'){
     def mvnHome = tool name: 'Maven', type: 'maven'
    sh "${mvnHome}/bin/mvn clean package"
  }
  stage("publish to s3") {
   s3Upload acl: 'Private', bucket: 's3-artifactsforjenkins', cacheControl: '', excludePathPattern: '/target', file: '', includePathPattern: '**/target/*.war', metadatas: [''], redirectLocation: '', sseAlgorithm: '', tags: '', text: '', workingDir: '' 
  }
    stage("E-mail notification"){
    mail bcc: '', body: 'Your build has been done please check the results.', cc: '', from: '', replyTo: '', subject: 'Jenkins Project-WarPipeline', to: 'sidharthvijayakumar7@gmail.com' 
  }
 
}
