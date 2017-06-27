# devnet2449
This is a repo to accompany the DevNet 2449 Session for Cisco Live

To Follow along the exercises on your own you will need:

- Git client
- VirtualBox 5.0.28
- Docker 1.13.1
- Vagrant 1.8.7
- cdrtools (in particular mkisofs)
- a build environment (e.g. compiler, make, ...), suggest to use MacPorts or Brew if running on a Mac
- Clone the [repository from GitHub](https://github.com/ios-xr/iosxrv-x64-vbox)
- [IOS XE image](https://software.cisco.com/download/type.html?mdfid=284364978&catid=null) from Cisco.com, then go to IOS XE Software and download the Denali-16.5.1 or higher .iso file)

1. Clone the following Git repository:
   `git clone https://github.com/ios-xr/iosxrv-x64-vbox && cd iosxrv-x64-vbox`

2. Create the Vagrant box image build by running the following command.

	`iosxe_iso2vbox.py -v ~/Downloads/<csr_iso_file>`

   This may take a while.

3. Install this image to vagrant

	`vagrant box add --name csr <csr_box_file_created_on_step_2>`

5. Make sure that the Vagrant box name matches the one configured in the Vagrantfile

6. Ensure you have the required tools installed

	https://github.com/dmfigol/devnet2449.git

7. run `make` to create the ISO files with the router configurations

8. Bring up the routers using `vagrant up` (brings up both) or `vagrant up R1` to only start R1

you can see the setup.sh script to bring up the router and docker container as in the session
