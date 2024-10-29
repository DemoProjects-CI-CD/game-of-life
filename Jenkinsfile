pipeline {
    agent {label 'MVN'}
    stages {
        stage (vcs) {
            steps {
                git branch: 'Master',
                    url: 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        stage (package) {
            tools {
                jdk 'JDK-8'
            }
            steps {
                sh 'mvn package'
            }
        }
        stage ('Post Build') {
           steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
           }
        }
    }
}