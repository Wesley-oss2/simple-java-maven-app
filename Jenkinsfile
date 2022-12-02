node {
def mvnHome = tool 'Maven3'
    stage ("checkout")  {
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-lab-Cred', url: 'https://github.com/Wesley-oss2/simple-java-maven-app']]])
    }
}

stage ('build')  {
    sh "${mvnHome}/opt/mvn clean install -f MyWebApp/pom.xml"
    }

stage ('Code Quality scan')  {
       withSonarQubeEnv('SonarQube') {
       sh "${mvnHome}/bin/mvn -f MyWebApp/pom.xml sonar:sonar"
        }
   }
