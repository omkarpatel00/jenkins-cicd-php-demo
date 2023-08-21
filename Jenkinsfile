pipeline {
    agent any
    
    stages {
        stage('SSH Connection') {
            steps {
                script {
                    // Define the SSH private key credential ID
                    def sshCredentialId = 'remote_host'
                    
                    // Define the SSH command to execute on the remote host
                    def sshCommand = "ssh -i /var/lib/jenkins/.ssh/id_rsa" +
                                     " -o StrictHostKeyChecking=no" +
                                     " ubuntu@182.18.184.71 "
                    
                    // Execute the SSH command
                    sh sshCommand
                }
            }
        }
        
        stage('git clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[credentialsId: 'omkarpatel00', url: 'https://github.com/omkarpatel00/jenkins-cicd-php-demo.git']]])
            }
        }
        
               stage('Deploy to Host') {
            steps {
                script {
                    def sshCredentialId = 'remote_host'
                    def ec2PublicIP = '182.18.184.71'
                    
                    // SSH command to deploy files to the EC2 instance
                    def sshDeployCommand = "ssh -i /home/ubuntu/.ssh -o StrictHostKeyChecking=no ubuntu@${ec2PublicIP} 'scp -rp /var/lib/jenkins/workspace/PHP-Demo/* /var/www/html/'"
                    
                    sh sshDeployCommand
                }
            }
        }
    }
}
