Estação
=========

Esse "role" do Ansible faz configurações iniciais em um computador com Debian 13 instalado. Ele instala uma suíte de programas comumente usados, configura o firewall, ssh e os navegadores Firefox e Chrome. 
Essas tarefas são as que são comumente feitas após se formatar o computador, de forma a automatizar o processo.

Requisitos
------------
Note que esse código foi testado somente no Debian 13 KDE, e não foi testado em outras distribuições.


Instalação e configuração
--------------
A configuração da estação de trabalho é realizada de forma remota, via SSH. É preciso configurar a sua estação
para então poder instalar.

Ansible e pipx. Instale o pipx com 

    $ sudo apt install pipx python3 python3-pip
    
e depois instale o Ansible com as dependências completas com 

    $ pipx install --include-deps ansible.
    
Para acessar os computadores, é preciso instalar o sshpass: 

    $ sudo apt install sshpass.

Adicione o nome ou endereço IP do computador que será configurado no inventário. Favor seguir o modelo no inventário, ou seja, definir o setor antes de definir o nome da máquina.

    all:
        children:
            recepcao:
                hosts:
                    gabinete:

Nesse exemplo, gabinete é o nome do computador e ele usará o IP obtido via DNS.
Verifique se é possível alcançar as máquinas via ansible, ou seja, se elas respondem ao ping:

    ansible all -m ping -i inventory.yml

Aplique o playbook com o comando:

    ansible-playbook -u suportecamara --askbecome playbook.yml -i inventory.yml --diff

Após o playbook terminar sem erros, reinicie a estação de trabalho e faça login.

Licença
-------

BSD

Autoria
------------------

Setor de tecnologia da informação da Câmara Municipal de Tapira.
