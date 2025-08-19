Estação
=========

Esse "role" do Ansible faz configurações iniciais em um computador com Debian 13 instalado. Ele instala uma suíte de programas comumente usados, configura o firewall, ssh e os navegadores Firefox e Chrome. 
Essas tarefas são as que são comumente feitas após se formatar o computador, de forma a automatizar o processo.
Note que esse código foi testado somente no Debian 13 KDE, e não foi testado em outras distribuições.

Requisitos
------------

Ansible e pipx. Instale o pipx com $ sudo apt install pipx python3 python3-pip, e depois instale o Ansible com as dependências completas com $ pipx install --include-deps ansible.
Para acessar os computadores, é preciso instalar o sshpass: $ sudo apt install sshpass.


Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Exemplo de playbook
----------------

Nesse comando, deve-se usar os parâmetros corretos na hora de chamar o Playbook. Deve-se tomar cuidado caso o usuário do seu computador seja diferente do usuário que está cadastrado como usuário do suporte. 
Lembre-se de usar --ask-become e digitar a senha do usuário do suporte, pois o Debian precisa de permissão de sudo para poder executar os comandos.

O playbook pode ser chamado com: 
    
    ansible-playbook -i inventory.yml playbook.yml -u usuariosuporte --ask-become

    - hosts: all
      become: yes
      roles:
        - estacao

Licença
-------

BSD

Autoria
------------------

Setor de tecnologia da informação da Câmara Municipal de Tapira.
