pipeline {
    agent { label 'workstation'}

    stages{
        stage('Download Dependencies'){
            steps {
            sh 'npm install'
            }
        }

        stage('Code Quality'){
            steps {
            sh 'sonar-scanner -Dsonar.host.url=http://172.31.81.125:9000 -Dsonar.login=admin -Dsonar.password=Canada1991$ -Dsonar.projectKey=backend'
            }
            }
        stage('test cases'){
            steps {
            // ideally in enterprise we have test case
            // sh 'npm test'
            echo 'CI'
            }
            }
        stage('release'){
                    steps {
                    // ideally in enterprise we have test case
                    // sh 'npm test'
                    echo 'CI'
                    }
                    }
       }
}
