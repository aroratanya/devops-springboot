node {
    def mvnHome
    stage('Prepare') {
        git url: 'git@github.com:aroratanya/devops-springboot.git',branch:'develop'
        mvnHome = tool 'mvn'
    }
    stage('Build') {
    
    sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
    
    
}

stage('Unit Test') {
junit '**/target/surefire-reports/TEST-*.xml'
archive 'target/*.jar'
}
  stage('Integration Test') {
   
    sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean verify"
    
    
    }
    stage('Sonar') {
  
    	sh "'${mvnHome}/bin/mvn' sonar:sonar"
    
    
    }
   
    
    }