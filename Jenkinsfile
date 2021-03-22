pipeline{
   agent any
   tools{
      maven 'maven'
      jdk 'JDK11'
   }
  stages {
      stage('Maven Build'){
          steps{
                   sh 'mvn -B -DskipTests clean package'
          }
      }
      stage('Maven Test'){
            steps{
                   sh 'mvn test'
            }
            post{
            always{
                junit 'target/surefire-reports/*.xml'
            }
        }
        }
     stage('SonarQube analysis') {
            agent any
            steps {
                 withSonarQubeEnv('sonar-server') {
                 sh 'java -version'
                 sh 'mvn sonar:sonar'
              }
            }
          }
     stage('Quality gate') {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
