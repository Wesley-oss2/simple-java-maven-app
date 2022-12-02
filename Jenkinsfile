node {
dev Home = tool name: 'Maven3', type: 'maven'
    stage ("checkout")  {
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-lab-Cred', url: 'https://github.com/Wesley-oss2/simple-java-maven-app']]])
    
    }
 stage ('build')  {
    sh "${mvnHome}/bin/mvn clean install -f App.java"
    }
}
stage ('Code Quality scan')  {
       withSonarQubeEnv('SonarQube') {
       sh "${mvnHome}/bin/mvn -f App.java sonar:sonar"
        }
   }
