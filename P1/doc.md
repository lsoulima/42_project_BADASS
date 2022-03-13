# Install GNS3 on Ubuntu 20.04

Step 1: Add GNS3 PPA repository
    `sudo add-apt-repository ppa:gns3/ppa`

Step 2: Install GNS3 GUI & GNS3 Server
    `sudo apt update`                               
    `sudo apt -y install gns3-server gns3-gui`
    then --> YES --> YES

Step 3: Install IOU Support (Optional) ***IOU (IOS over Unix) is an internal Cisco tool for simulating the ASICs in Cisco Switches. This enables you to play with Layer 2 switching in your LABS***
    `sudo dpkg --add-architecture i386`
    `sudo apt update`
    `sudo apt -y install gns3-iou`

Step 4: Docker Support (Optional)
    `sudo apt -y update`
    `sudo apt -y install apt-transport-https ca-certificates curl gnupg-agent software-properties-common`
    `sudo apt remove docker docker-engine docker.io containerd runc                     //If you have older versions of Docker, remove it and its dependent packages`
    `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -       //Import Docker repository GPG key`
    `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`
    `sudo apt update`
    `sudo apt -y install docker-ce docker-ce-cli containerd.io`
    `sudo usermod -aG docker $USER  //Add your user account to docker group.`
    `newgrp docker`
    `docker version`
    After installing Docker and IOU, add your user to the following groups:
        for i in ubridge libvirt kvm wireshark docker; do
        sudo usermod -aG $i $USER
        done

Step 5: Launch GNS3 on Ubuntu 20.04
    `sudo gns3`
    config --> Run the appliances on my computer --> Next ... Finish

//https://computingforgeeks.com/how-to-install-gns3-on-ubuntu/
