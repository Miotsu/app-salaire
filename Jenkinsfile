  node{
      stage('Deploiement') {
          checkout scm
      }
      stage('Mise en place clé ssh'){

          '''
          apk add sshpass
          ssh-keygen -q -t rsa -N \'\' -f /root/.ssh/id_rsa
          sshpass -p \'isoadmin\' ssh-copy-id  -o stricthostkeychecking=no root@app-salaire.julien.form
          echo "app-salaire.julien.form" > hosts.yml
          '''
      }
      stage('Ansible') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
