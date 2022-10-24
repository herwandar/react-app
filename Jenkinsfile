node {
    checkout scm
        docker.image('node:lts-buster-slim').inside('-p 3000:3000') { 
            withEnv(['CI=true']){
                stage('build'){
                    checkout scm
                    sh 'npm install'
            }
                stage('Test') {
                checkout scm
                sh './jenkins/scripts/test.sh'
            }
            stage('Deliver') {
            checkout scm
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}