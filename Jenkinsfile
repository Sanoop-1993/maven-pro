node {
   
   stage('Code Checkout') { // for display purposes
    git credentialsId: 'githubid', url: 'https://github.com/Sanoop-1993/maven-pro.git'  
   }
   stage('Code Build') {
    withMaven(jdk: 'JDK-1.8', maven: 'maven-3.6.1') {
     sh 'mvn clean compile'
    }  
   }
   stage('Unit Test') {
       withMaven(jdk: 'JDK-1.8', maven: 'maven-3.6.1') {
        sh 'mvn test'
     }  
   }
   stage('SonarQube Analysis') {
       withMaven(jdk: 'JDK-1.8', maven: 'maven-3.6.1') {
       sh mvn verify sonar:sonar \
               -Dsonar.projectKey=maven-pro-sanoop \
               -Dsonar.organization=sanoop \
               -Dsonar.host.url=https://sonarcloud.io \
               -Dsonar.login=b2560983aea64fe53b1be6d437435bc7b05a0f15
       }
   } 
   stage('Archive to Jfrog') {
   } 
   stage('Docker Image') {
   } 
   stage('Deploy to Prods') {
   } 
}
