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
    sh "${mvnHome} sonar:sonar \
  -Dsonar.projectKey=java \
  -Dsonar.host.url=http://35.225.127.236:32545 \
  -Dsonar.login=27bb74029f34edf27f7171243b37e7c694f3350a"
    
  }
 
}

