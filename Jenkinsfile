node {
dev Home = tool name: 'Maven3', type: 'maven'
    stage ("checkout")  {
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-lab-Cred', url: 'https://github.com/Wesley-oss2/simple-java-maven-app']]])
    }
}

stage ('Compile-Package')  {
    // Get maven home path
    dev Home = tool name: 'Maven3', type: 'maven'
    sh "${mvnHome}/bin/mvn package"
    
    }

stage ('Code Quality scan')  {
       withSonarQubeEnv('SonarQube') {
       sh "${mvnHome}//opt/apache-maven-3.6.3 -f MyWebApp/pom.xml sonar:sonar"
        }
   }
