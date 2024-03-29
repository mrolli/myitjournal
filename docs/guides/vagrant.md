# Vagrant

Vagrant is a must have CLI tool to manage local virtual machines using
VirtualBox (or VMware Fusion or
[they-name-it](https://www.vagrantup.com/docs/providers)). You can script every
aspect of creating, provisioning, saving and destroying VMs. This makes this
tool perfect for DevOps testing locally on your machine or even out in a cloud.

See the [Vagrant Documentation](https://www.vagrantup.com/docs) for a primer.

## Installation

The installation process is well outlined at the [Download
Vagrant](https://www.vagrantup.com/downloads) page.

For **macOS users** the simplest is to use brew as Vagrant is a cask and there's
bash completion formula. Just run:

    brew install vagrant vagrant-completion

## VM config examples

@TODO

## Tips & Tricks / How to...

### Change names (VM name, hostname, ...)

There are at least the following levels of naming a virtual server depending on
the context:

* **Machine Name**: The name of the virtual server when running `vagrant status`
  or that you see when starting the VM: `Bringing machine 'label' up with
  'virtualbox' provider...`.
* **VM Name**: The name of the underlying VirtualBox Machine that you see in the
  Virtualbx GUI Client and that is used as the name for its subdir in your
  `VirtualBox VMs` directory or that you see when running `VBoxManage list vms`
* **Hostname**: The hostname that is set within the virtual machine AKA the
  running guest OS

The question inherently arises: How are these set by default and how can I
customize them?  
Well the
[documentation](https://www.vagrantup.com/docs/vagrantfile/machine_settings) is
not that clear about all this but fear not, you're covered with systematic
examples below.

**All these examples are run in a project directory named "myproject"** using
Vagrant-2.2.18 on VirtualBox-6.1.26r145957.

!!! abstract "Example 1: All defaults, e.g. only specifying the base box to use"
    ```ruby
    Vagrant.configure("2") do |config|
      config.vm.box = "geerlingguy/rockylinux8"
    end

    ```

    **Result:**

    Machine Name|VM Name|Guest OS Nostname $(hostname -f)
    -|-|-
    default|myproject_default_1632646458961_81073|localhost

    **Discussion:**
    Vagrant chooses <default> as the default name of the machine. The name on
    Virtualbox side is generated ([see generating code]) as
    `<DIRECTORY>_<MACHINE_NAME>_<TIMESTAMP>_<RANDOM_NUMBER>` unless explicitly
    set, see next examples. The hostname seems to be unchanged, e.g. the
    hostname of the basebox, localhost in the example.

    [see generating code]: https://github.com/hashicorp/vagrant/blob/main/plugins/providers/virtualbox/action/set_name.rb#L23-L30

---

!!! abstract "Example 2: Explicitly define a VM and set a machine name"
    ```ruby
    Vagrant.configure("2") do |config|
      config.vm.box = "geerlingguy/rockylinux8"

      # Explicitly define a vm; first argument is the machine name
      config.vm.define "webserver"
    end
    ```

    **Result:**

    Machine Name|VM Name|Guest OS Nostname $(hostname -f)
    -|-|-
    webserver|myproject_webserver_1632646458961_81073|localhost

    **Discussion:** Now the default machine name has been overwritten with
    `webserver`. This also opens the door to mult-machine setups. As you can see
    the new machine name is also found in the generated vm name that is visible
    when running `VBoxManage list vms` or in the VirtualBox GUI client.

---

!!! abstract "Example 3: Set the hostname of the Guest OS"
    ```ruby
    Vagrant.configure("2") do |config|
      config.vm.box = "geerlingguy/rockylinux8"

      # Explicitly define a vm; first argument is the machine name
      config.vm.define "webserver"
      config.vm.hostname = "web01.test.com"
    end
    ```

    **Result:**

    Machine Name|VM Name|Guest OS Nostname $(hostname -f)
    -|-|-
    webserver|myproject_webserver_1632646458961_81073|web01.test.com

    **Discussion:**
    Vagrant now sets the hostname within the guest OS to the specified value:
    ```bash
    [vagrant@web01 ~]$ hostname -s
    web01
    [vagrant@web01 ~]$ hostname -f
    web01.test.com
    ```

---

!!! abstract "Example 4: Set the hostname of the Guest OS"
    ```ruby
    Vagrant.configure("2") do |config|
      config.vm.box = "geerlingguy/rockylinux8"

      # Explicitly define a vm; first argument is the machine name
      config.vm.define "webserver"
      config.vm.hostname = "web01.test.com"
      config.vm.provider :virtualbox do |vb|
        vb.name = "webserver01"
      end
    end
    ```

    **Result:**

    Machine Name|VM Name|Guest OS Nostname $(hostname -f)
    -|-|-
    webserver|webserver01|web01.test.com

    **Discussion:** This example, in addition, is setting the name on the
    virtualbox provider object, which results in a renamed VM. The VM no longer
    has its name generated as described in example 1, but the name is now set
    explicitly, see GUI client or `VBoxManage list vms`.

    But wait... there's one more! Instead of setting `name` on the provider
    object, it's possible to have Vagrant call `VBoxManage` and have it set the
    name. This overrides all of the previous methods:
    ```ruby
      config.vm.provider :virtualbox do |vb|
        vb.name = "webserver01"
        vb.customize ["modifyvm", :id, "--name", "web01"]
      end
    ```
    In the above example, the final name of the VM will be `web01`.

!!! success "Conclusion"
    It makes sense to use of these powerful possibilities of naming things.
    Especially it is useful to use them to namespace the virtual machines because
    when approaching the setup from the VM perspective you can map the VM instance
    to a project and the servers there in. Therefore if you set it to an absolute
    name using `VBoxManage`, I'd suggest to namespace it to the project it belongs
    to, something like "myproject_webserver01" or something like that.

### Change machine settings like RAM, network cards, ...

These configuration options are provider-specific. For VirtualBox have a look on
the respective [page in the
documentation](https://www.vagrantup.com/docs/providers/virtualbox/configuration).
Summarized with two examples, it's possible to set almost everything by calling
`VBoxManage` from within the Vagrantfile. The vb.customize directive calls
`VBoxManage` and the contents of the array specified as its argument are passed
straight to it. See `VBoxManage --help` for all the possible targets - there a
lot!

!!! abstract "Example modifying apects of a virtualbox machine"
    ```ruby
    config.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--memory", "384"]
      vb.customize ["modifyvm", :id, "--nic3", "intnet"]
      vb.customize ["modifyvm", :id, "--nic4", "intnet"]
    end

    # There are some convenience shortcuts for memory and CPU settings:
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 2
    end
    ```

### Setting a fixed port for SSH forwwards

Normally the ssh from the guest is automatically forwarded to port 2222 on the
host. When port the latter port is already in use for another running VM, the
next free post >2222 is choesen. This makes the port dependent of the order you
start the VMs. While most of the time this is not a problem, you sometimes still
want a fixed set of IPs for a project. Add this to your `Vagrantfile` for each
machine you like to fix the forwarded SSH port:

    ```ruby
      config.vm.network "forwarded_port", guest: 22, host: 12345, id: "ssh"
    ```

Source was [this
ticket](https://realguess.net/2015/10/06/overriding-the-default-forwarded-ssh-port-in-vagrant/)
and this [blog entry](https://realguess.net/2015/10/06/overriding-the-default-forwarded-ssh-port-in-vagrant/).
