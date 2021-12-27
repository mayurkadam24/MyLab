pipeline {

agent any

tools{
maven 'maven-3.8.4'
}

environment {

ArtifactId = readMavenPom().getArtifactId()
Version = readMavenPom().getVersion()
GroupId = readMavenPom().getGroupId()

}

stages {

stage ('Build') {

steps {

sh 'mvn clean package install'

}

}

stage ('Test') {

steps {

sh 'echo "This is the Test stage step"'

}

}

stage ('Publish to Nexus') {

steps {

    script {

    def NexusRepo = Version.endsWith("SNAPSHOT") ? "VinaysDevOpsLabs-SNAPSHOT" : "VinaysDevOpsLabs-RELEASE"

    nexusArtifactUploader artifacts: [[artifactId: "${ArtifactId}", classifier: '', file: "target/${ArtifactId}-${Version}.war", type: 'war']], credentialsId: '4a2b8b28-6dab-414e-b500-f7b74e926585', groupId: "${GroupId}", nexusUrl: 'http://3.15.172.190:8081', nexusVersion: 'nexus3', protocol: 'http', repository: "${NexusRepo}", version: "${Version}"
}

}

}

stage ('Deploy') {

steps {
sh 'echo "This is the Deploy stage step"'

    }

}

}

}