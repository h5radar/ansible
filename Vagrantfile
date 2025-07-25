Vagrant.configure("2") do |config|

  config.vm.define "api1.h5radar.com" do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-24.04"
    ubuntu.vm.provider :libvirt do |lv|
      lv.title = 'h5radar-api'
    end
  end
  config.vm.define "app1.h5radar.com" do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-24.04"
    ubuntu.vm.provider :libvirt do |lv|
      lv.title = 'h5radar-app'
    end
  end
  config.vm.define "iam1.h5radar.com" do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-24.04"
    ubuntu.vm.provider :libvirt do |lv|
      lv.title = 'h5radar-iam'
    end
  end

  config.vm.provider :libvirt do |lv|
    lv.cpus = 4
    lv.memory = 4096
    lv.video_type = 'virtio'
    lv.graphics_type = 'spice'
    lv.default_prefix = ''
    lv.qemu_use_session = false
  end

  config.vm.synced_folder "..", "/vagrant", type: "rsync", disabled: true

  config.vm.provision "ansible" do |ansible|
    ansible.config_file = "ansible.cfg"
    ansible.playbook = "main.yml"
    ansible.host_vars = {
      "api1.h5radar.com" => {"image" => "ubuntu24" },
      "app1.h5radar.com" => {"image" => "ubuntu24" },
      "iam1.h5radar.com" => {"image" => "ubuntu24" }
    }
    ansible.groups = {
      "api_h5radar_servers" => ["api1.h5radar.com"],
      "api_h5radar_servers:vars" => {"h5radar_api__cert_type" => 'letsselfsign'},
      "app_h5radar_servers" => ["app1.h5radar.com"],
      "app_h5radar_servers:vars" => {"h5radar_app__cert_type" => 'letsselfsign'},
      "iam_h5radar_servers" => ["iam1.h5radar.com"],
      "iam_h5radar_servers:vars" => {"h5radar_iam__cert_type" => 'letsselfsign'}
    }
  end
end
