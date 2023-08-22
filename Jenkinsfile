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
                withCredentials([sshUserPrivateKey(credentialsId: 'remote_host', keyFileVariable: 'PRIVATE_KEY')]) {
                    script {
                        sshagent(['remote_host']) {
                            sh '''
                                scp -i $PRIVATE_KEY -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/PHP-Demo/index.php ubuntu@182.18.184.71:/var/www/html/
                            '''
                        }
                    }
                }
            }
        }
    }
}
