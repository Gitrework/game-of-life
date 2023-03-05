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
                  tool { jdk 'JAVA-8-JDK' }
                  steps{
                        sh 'mvn package'
                  }                  
            }
            stage('buld') {
                  steps{
                        archiveArtifacts artifacts:  '**/*.txt',
                                 onlyIfSuccessful: true
                        junit testResults: '**/surefire-reports/TEST-*.xml'
                  }
            }

      }
}