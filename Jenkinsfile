node {
def mvnHome = tool 'Maven3'
    stage ("checkout")  {
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-lab-Cred', url: 'https://github.com/Wesley-oss2/simple-java-maven-app']]])
    }
}

stage ('build')  {
    sh "${mvnHome}/opt/apache-maven-3.6.3 clean install -f MyWebApp/pom.xml"
    }

stage ('Code Quality scan')  {
       withSonarQubeEnv('SonarQube') {
       sh "${mvnHome}//opt/apache-maven-3.6.3 -f MyWebApp/pom.xml sonar:sonar"
        }
   }
