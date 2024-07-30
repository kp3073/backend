pipeline {
    agent { label 'workstation'}

    stages{
         stage('Download Dependencies'){
             steps {
                    sh 'npm install'
                    echo 'CI'
                    }
                }
         stage('Code Quality'){
          when {
               allof{
               branch 'main'
               expression { env.TAG_NAME != env.BRANCH_NAME }
                    }
                }
            steps {
                    sh 'sonar-scanner -Dsonar.host.url=http://172.31.81.125:9000 -Dsonar.login=admin -Dsonar.password=Canada1991$ -Dsonar.projectKey=backend'
                    }
                }
         stage('test cases'){
          when {
                   allof{
                   branch 'main'

                  }
                  }
            steps {
                    // ideally in enterprise we have test case
                    // sh 'npm test'
                    echo 'CI'
                    }
                }
         stage('release'){
         when {
             expression {env.TAG_NAME ==~ ".*"}
         }
            steps {
                    // ideally in enterprise we have test case
                    echo 'CI'
                    }
                }
       }
}
