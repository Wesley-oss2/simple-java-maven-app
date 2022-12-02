node {
def mvnHome = tool 'Maven3'
    stage ("checkout")  {
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-lab-Cred', url: 'https://github.com/Wesley-oss2/simple-java-maven-app']]])
    }
