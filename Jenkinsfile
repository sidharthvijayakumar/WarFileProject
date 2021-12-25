node{
  stage('SCM Checout'){
   
  git 'https://github.com/sidharthvijayakumar/WarFileProject'
  }
  stage('Build'){
     def mvnHome = tool name: 'Maven', type: 'maven'
    sh "${mvnHome}/bin/mvn clean package"
  }
  stage('SonarQube analysis') {
    withSonarQubeEnv(credentialsId: '27bb74029f34edf27f7171243b37e7c694f3350a', installationName: 'My SonarQube Server') { // You can override the credential to be used
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
    }
 
}

