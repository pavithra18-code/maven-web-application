
node{
  
  properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
  
echo "job name is: ${env.JOB_NAME}"
echo "build number is: ${env.BUILD_NUMBER}"
echo "node name is: ${env.NODE_NAME}"
echo "jenkins home dir is: ${env.JENKINS_HOME}"

def mavenHome = tool name: 'maven3.9.8'

stage('Checkoutcode'){
git branch: 'development', credentialsId: '14bd4d6b-e2c2-47fb-b79f-af88366de933', url: 'https://github.com/pavithra18-code/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
  
/*
stage('ExecuteSonarqubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('uploadArtifcaysIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppInTomcatServer'){
sshagent(['96c3f7c3-9fd2-42d8-8107-231c97d48aac']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war 
ec2-user@172.31.24.11:/opt/apache-tomcat-9.0.98/webapps"
}
}
*/
  
}
