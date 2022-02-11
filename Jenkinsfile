  node{
      stage('Deploiement') {
          checkout scm
      }
      stage('Connexion ssh'){
            
        sh 'echo "127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4" > /etc/hosts'
        sh 'echo "::1         localhost localhost.localdomain localhost6 localhost6.localdomain6" >> /etc/hosts'
        sh 'echo "192.168.11.103 app-salaire.julien.form" >> /etc/hosts'
        sh 'apk add sshpass'
        sh 'rm -fr /root/.ssh/*'
        sh 'ssh-keygen -q -t rsa -N \'\' -f "/root/.ssh/id_rsa"'
        sh 'sshpass -p \'isoadmin\' ssh-copy-id  -o stricthostkeychecking=no "root@app-salaire.julien.form"'
        
            
      }
       
      stage('Ansible') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
