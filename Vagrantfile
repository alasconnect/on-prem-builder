Vagrant.configure('2') do |config|
  config.vm.provider 'hyperv' do |h, override|
    h.memory = 2048
    h.maxmemory = 6144
    h.cpus = 2

    override.vm.synced_folder '.', '/vagrant', type: 'smb', mount_options: ['vers=3.0'], smb_host: ENV['VAGRANT_SMB_HOST'], smb_username: ENV['VAGRANT_SMB_USERNAME']
  end

  config.vm.define 'default', primary: true do |default|
    default.vm.box = 'centos-7.6'
    default.vm.box_url = 'https://artifactory.alasconnect.com/artifactory/api/vagrant/vagrant/centos-7.6'
    default.vm.hostname = 'on-prem-builder'

    default.vm.provider 'hyperv' do |h|
      h.vmname = 'on-prem-builder'
    end
  end
end
