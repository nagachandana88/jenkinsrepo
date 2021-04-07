pipeline {
   //agent {label 'slavejobs'}
    agent any
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven-3.6.3"      
    }
  stages {
     stage('git clone') {
      steps {
       git credentialsId: 'github', url: 'https://github.com/nagachandana88/pro1.git'
                  }
     }
    stage('Build clean') {
        steps {
         sh 'mvn clean'
        }
    }
 stage('Build compile') {
     steps {
         sh 'mvn compile'
        }
    }
  stage('sonarqube codescan'){
     steps{
            sh'mvn sonar:sonar \
 		        -Dsonar.projectKey=com.ksapp:ks \
  		        -Dsonar.host.url=http://18.188.170.202:9000 \
  		        -Dsonar.login=4f8839828580c81aa23905e2e9c3b9ee7b717875 '
          }
   }
 stage('Build test') {
       steps {
           sh 'mvn test'
        }
    }
 stage('Build package') {
        steps {
         sh 'mvn package'
        }
    }
 stage('Build deploy') {
       steps{
           sh 'mvn deploy'
        }
    }
 }
}
