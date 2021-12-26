pipeline {

agent any

tools{
maven 'maven-3.8.4'
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

stage ('Deploy') {

steps {
sh 'echo "This is the Deploy stage step"'

    }

}

}

}