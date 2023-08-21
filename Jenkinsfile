pipeline {
    agent any

    stages {
        stage('SSH Connection') {
            steps {
                script {
                    def sshCredentialId = 'remote_host'
                    def ec2PublicIP = '182.18.184.71'

                    sh "ssh -i ${sshCredentialId} -o StrictHostKeyChecking=no ubuntu@${ec2PublicIP} 'mkdir kavya-new'"
                }
            }
        }

        stage('Git Clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[credentialsId: 'omkarpatel00', url: 'https://github.com/omkarpatel00/jenkins-cicd-php-demo.git']]])
            }
        }

        stage('Deploy to Host') {
            steps {
                script {
                    def sshCredentialId = 'remote_host'
                    def ec2PublicIP = '182.18.184.71'

                    sh "scp -i /home/ubuntu/.ssh/id_rsa -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/PHP-Demo/* ubuntu@${ec2PublicIP}:/var/www/html/"
                }
            }
        }
    }
}
