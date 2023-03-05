pipeline{
      agent { label 'SONAR-NODE' }
      tool {
            jdk 'JAVA-8-JDK'
      }       
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
                        archiveArtifacts artifacts:  '**/*.txt',
                                 onlyIfSuccessful: true
                        junit testResults: '**/surefire-reports/TEST-*.xml'
                  }
            }

      }
}