pipeline {
    agent any

    stages {
        stage('Git Clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[credentialsId: 'omkarpatel00', url: 'https://github.com/omkarpatel00/jenkins-cicd-php-demo.git']]])
            }
        }

        stage('Deploy HTML') {
            steps {
                script {
                    sshagent(['SSH_CREDENTIAL_ID']) {
                        sh '''
                            scp /var/lib/jenkins/workspace/PHP-Demo/index.php ubuntu@182.18.184.71:/var/www/html/
                        '''
                    }
                }
            }
        }
    }
}
