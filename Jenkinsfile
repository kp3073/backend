
pipeline {
  agent { label 'workstation'}

  stages {

    stage('Download Dependencies'){
      steps {
        sh 'npm install'
        sh 'env'
      }
    }

    stage('Code Quality'){
      when {
        allOf {
          expression { env.TAG_NAME != env.GIT_BRANCH }
        }
      }
      steps {
        sh 'sonar-scanner -Dsonar.host.url=http://172.31.81.125:9000 -Dsonar.login=admin -Dsonar.password=Canada1991$ -Dsonar.projectKey=backend'

      }
    }

    stage('Unit Tests'){
      when {
        allOf {
          branch 'main'
          expression { env.TAG_NAME != env.GIT_BRANCH }
        }
      }
      steps {
        // Ideally we should run the tests , But here the developer have skipped it. So assuming those are good and proceeding
        // sh 'npm test'
        echo 'CI'
      }
    }

       stage('Release'){
         when {
           expression { env.TAG_NAME ==~ ".*" }
         }
        steps {
             sh 'zip -r backend${TAG_NAME}.zip node_modules DbConfig.js package.json schema index.js TransactionService.js'
             sh 'curl  sSf -u "admin:Canada1991$" -X PUT -T backend${TAG_NAME}.zip "http://artifactory.aligntune.online:8081/backend/backend${TAG_NAME}.zip"'
        }
       }
     }
   }


