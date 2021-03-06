# Using Ansible to Template a Kubeadm Configuration File with etcd Support

These files provide an example of how to use Ansible's `template` module to create a Kubeadm 1.11 configuration file (with local etcd support) from a Jinja2 template. The template and Ansible playbook were tested using Ansible 2.5 on Fedora 27, but should work on any recent version of Ansible on any supported platform.

**NOTE:** At this time, the `kubeadm` configuration files generated by this playbook have _not_ been verified to create a working, conformant Kubernetes cluster. Consider them to be for demonstration purposes only.

## Contents

* **1-kubeadm.conf.j2**: This Jinja2 template contains the framework for a Kubeadm configuration file. This template is for the first stacked master.

* **2-kubeadm.conf.j2**: This Jinja2 template contains the framework for a Kubeadm configuration file. This template is for the second stacked master.

* **3-kubeadm.conf.j2**: This Jinja2 template contains the framework for a Kubeadm configuration file. This template is for the third stacked master.

* **ansible.cfg**: This is an Ansible configuration file. You may need to edit this file based on the target systems you're using with this environment.

* **README.md**: The file you're currently reading.

* **template.yml**: This Ansible playbook takes a series of variables along with the `*-kubeadm.conf.j2` Jinja2 templates. The output is three different `kubeadm` configuration files.

## Instructions

These instructions assume that you have Ansible installed and functioning correctly on your system.

1. Place the files from the `ansible/kubeadm-etcd-template` directory of this GitHub repository into a directory on your local system. You can clone the entire "learning-tools" repository (using `git clone`) or just download the specific files from the `ansible/kubeadm-etcd-template` folder.

2. (Optional) Edit `template.yml` to specify different values for the variables defined in the playbook.

3. This environment was tested using a CentOS-based AMI running on AWS, and as such uses the EC2 dynamic inventory module. Edit `inventory/ec2.ini` and `inventory/hosts` as needed to ensure that this environment will work for your specific inventory. You may also need to edit `ansible.cfg`, depending on the Linux distribution you choose to use.

4. Run `ansible-playbook template.yml` to generate the three different `kubeadm` configuration files. They will be rendered in the same directory as `kubeadm-cfg-first.yaml`, `kubeadm-cfg-second.yaml`, and `kubeadm-cfg-third.yaml`, respectively.

Enjoy!

## License

This content is licensed under the MIT License.
