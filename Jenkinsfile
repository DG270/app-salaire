node{
      stage('Clone') {
          checkout scm
      }
      stage('Connexion ssh'){

          '''
          apk add sshpass
          ssh-keygen -q -t rsa -N \'\' -f /root/.ssh/id_rsa
          sshpass -p \'P@ss4ing\' ssh-copy-id  -o stricthostkeychecking=no root@app-salaire.dimitri.form
          '''
      }
      stage('Playbook') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
