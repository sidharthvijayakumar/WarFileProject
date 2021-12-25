node{
  stage('SCM Checout'){
   
  git 'https://github.com/sidharthvijayakumar/WarFileProject'
  }
  stage('Build'){
     def mvnHome = tool name: 'Maven', type: 'maven'
    sh "${mvnHome}/bin/mvn clean package"
  }
  stage('SonarQube analysis') {
    def mvnHome = tool name: 'Maven', type: 'maven'
    sh "${mvnHome} sonar:sonar"
    
  }
 
}

