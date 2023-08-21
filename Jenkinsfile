pipeline {
    agent any

    stages {
        stage('SSH Connection') {
            steps {
                script {
                    def sshCredentialId = 'remote_host'
                    def ec2PublicIP = '182.18.184.71'

                    sh "ssh -i /home/ubuntu/.ssh -o StrictHostKeyChecking=no ubuntu@${ec2PublicIP} 'mkdir test-dir'"
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

                    sh "ssh -i /home/ubuntu/.ssh -o StrictHostKeyChecking=no ubuntu@${ec2PublicIP} 'scp -rp /var/lib/jenkins/workspace/PHP-Demo/* ubuntu@${ec2PublicIP}:/var/www/html/'"
                }
            }
        }
    }
}
