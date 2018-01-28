# brewhouse
Provisions server(s) in EC2 to run R packages.


#Notes to install ansible (on Mac)
cd /tmp
git clone https://github.com/ansible/ansible.git
cd ansible
pip install -r requirements.txt
python setup.py install

sudo mkdir /etc/ansible
cd /etc/ansible
wget https://raw.github.com/ansible/ansible/devel/contrib/inventory/ec2.py 
wget https://raw.github.com/ansible/ansible/devel/contrib/inventory/ec2.ini

export ANSIBLE_HOSTS=/etc/ansible/ec2.py
export EC2_INI_PATH=/etc/ansible/ec2.ini

#after updating 
#/etc/ansible/ansible.cfg  (inventory      = /etc/ansible/ec2.py)

#test things out
ansible -vvv all -u ubuntu -m ping

#ansible-galaxy install geerlingguy.java
#ansible-galaxy install tersmitten.r
#ansible-galaxy install tersmitten.rstudio-server

#Tunnel local vnc connection to remote host
#ssh -i ~/.ssh/alphahops.pem -L 5900:127.0.0.1:5900 -N ubuntu@ec2-54-90-86-108.compute-1.amazonaws.com


#IBController 
telnet <host> 7462
ENABLEAPI

#Create vault
ansible-vault create vault.yml
ansible-vault edit vault.yml (in brewhouse/conf/vars)
Requires:
	vault_IB_Username:
	vault_IB_Password:
	vault_rstudio_username:
	vault_rstudio_password:
	vault_db_username:
	vault_db_password:
	vault_EDGAR_APIKEY:
	vault_INTRINIO_USER:
	vault_INTRINIO_PASS:
	vault_WUNDERGROUND_KEY:
	vault_QUANDL_KEY:

#edit /etc/ansible.cfg
vault_password_file = ~/.ansible_vault_pass




