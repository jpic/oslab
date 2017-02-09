Requirements: ansible, vagrant, virtualbox

vagrant gem install vagrant-vbguest
vagrant plugin install vagrant-cachier

Start controller, compute0 and compute1: `vagrant up --no-provision`
You MUST use --no-provision

Run ansible provisionning again: `vagrant provision`

Note: you need vagrant master: https://github.com/mitchellh/vagrant/issues/8269
