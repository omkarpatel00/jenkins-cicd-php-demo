pipeline {
    agent any
    stages {
        stage('git clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[credentialsId: 'omkarpatel00', url: 'https://github.com/omkarpatel00/jenkins-cicd-php-demo.git']]])
            }
        }
        stage('Deploy to Host') {
            steps {
                script {
                    sshagent(['remote_host']) {
                        sh 'scp -rp /var/lib/jenkins/workspace/demo-php-github/* ubuntu@182.18.184.71:/var/www/html/'
                    }
                }
            }
        }
    }
}
