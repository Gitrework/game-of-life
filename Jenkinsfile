pipeline{
      agent { label 'SONAR-NODE' }
      stages {
            stage('vcs') {
                  steps{
                        git url: 'https://github.com/Gitrework/game-of-life.git',
                            branch: 'master'
                  }
            } 
            stage('package') {
                  steps{
                        sh 'mvn package'
                  }                  
            }
            stage('buld') {
                  steps{
                        archiveArtifacts artifacts: '**/target/spring-petclinic-3.0.0-SNAPSHOT.jar',
                                 onlyIfSuccessful: true
                        junit testResults: '**/surefire-reports/TEST-*.xml'
                  }
            }

      }
}