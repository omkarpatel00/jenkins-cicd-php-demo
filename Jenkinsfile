pipeline {
    agent any

    stages {
         stage('Git Clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[credentialsId: 'omkarpatel00', url: 'https://github.com/omkarpatel00/jenkins-cicd-php-demo.git']]])
            }
        }

        stage('Deploy PHP App') {
            steps {
                script {
                    sshagent(['remote_host']) {
                        sh '''
                            scp -r /var/lib/jenkins/workspace/PHP-Demo ubuntu@182.18.184.71:/var/www/html/
                        '''
                    }
                }
            }
        }
    }
}
