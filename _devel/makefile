vagrant_up :
	vagrant up --no-provision

vagrant_provision :
	rm -rf tmp_roles
	rm -f ansible_gocd_agent
	mkdir -p tmp_roles
	git clone git@github.com:shaikhfaisal/ansible_gocd_server.git tmp_roles/ansible_gocd_server
	ln -s ../ ansible_gocd_agent
	vagrant provision
	rm -rf tmp
	rm -f ansible_gocd_agent

clean :
	vagrant destroy

test :	vagrant_up vagrant_provision

travis_ci:
	sudo apt-get install software-properties-common
	sudo apt-add-repository -y ppa:ansible/ansible
	sudo apt-get update
	sudo apt-get install -y ansible
	ln -s ../ ansible_gocd_agent
	ansible-playbook -c local -e "hosts=127.0.0.1" test.yml
	rm -f ansible_gocd_agent
