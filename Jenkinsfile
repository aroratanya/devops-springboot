node {
    def mvnHome
    stage('Prepare') {
        git url: 'git@github.com:aroratanya/devops-springboot.git',branch:'develop'
        mvnHome = tool 'maven'
    }
    stage('Build') {
    
    bat "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
    
    
}

stage('Unit Test') {
junit '**/target/surefire-reports/TEST-*.xml'
archive 'target/*.jar'
}
  stage('Integration Test') {
   
    bat "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean verify"
    
    
    }
    stage('Sonar') {
  
    	bat "'${mvnHome}/bin/mvn' sonar:sonar"
    
    
    }
   
    
    }