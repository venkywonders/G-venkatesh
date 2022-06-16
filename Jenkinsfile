pipeline {
    agent 'any'
  stages {
      stage('git-clone') {
          steps {
              sh '''
              rm -rf G-venkatesh
              pwd
              ls -a -ll
              git clone https://github.com/venkywonders/G-venkatesh.git
              ls -ll 
              '''
          }
      }
      stage('compile') {
          steps {
              sh '''
              pwd
              cd $WORKSPACE
              ls -ll
              cd G-venkatesh
              ls -ll
              mvn clean
              mvn compile
              '''
          }
      }
      stage('unit-test') {
          steps {
              sh '''
              pwd
              cd $WORKSPACE
              ls -ll
              cd G-venkatesh
              ls -ll
              mvn test
              '''
          }
      }
      stage('codquality') {
          steps {
              sh '''
              pwd
              cd $WORKSPACE
              ls -ll
              cd G-venkatesh
              ls -ll
              mvn sonar:sonar
              '''
          }
      }
      stage('packag') {
          steps {
              sh '''
              pwd
              cd $WORKSPACE
              ls -ll
              cd G-venkatesh
              ls -ll
              mvn package
              '''
          }
      }
      stage('artifactory deploy') {
          steps {
              sh '''
              curl -uadmin:AP9NJRGC5ZVBkYE5F4JKSH2Voju -T /c/Users/Lenovo/.jenkins/workspace/pipeline/G-venkatesh/target/hj-1.0.0.jar "http://localhost:8081/artifactory/devops-key/"
              '''
          }
      }
  }
}
