Instructions for Intro to DevOps Project
========================================

## Part 0 - Local Installation

1. Install VirtualBox
2. Install Vagrant
3. Install Packer
4. Install git

## Part I - Build Boxes with Packer

### To make an image for local development

From the packer-templates directory:

1. run `packer build -only=virtualbox-iso application-server.json`
2. run `cd virtualbox`
3. run `vagrant box add ubuntu-14.04.4-server-amd64-appserver_virtualbox.box --name devops-appserver`
4. run `vagrant up`
5. run `vagrant ssh` to connect to the server


### To make application server image for cloud

See full directions at: https://www.udacity.com/wiki/ud611

### To make control (CI and monitoring) server image for cloud

## Part II - Cloning, Developing and Running the web application

1. On your local machine go to the root directory of this repository

    run `git clone https://github.com/chef/devops-kungfu.git devops-kungfu`

2. Open http://localhost:8080 from your local machine to see the app running.

3. If you want to run tests on the app - 
    In the VM run:
    `cd devops-kungfu`
    To install app specific node packages: 
    `sudo npm install`
    Now you can run tests - `grunt -v`
                                     

### Troubleshooting

* If you encounter errors with Ubuntu version numbers not being available or checksum errors on Ubuntu and this repository is not yet updated, you can fix this by editing the contents of the `application-server.json` and `control-server.json` template files inside the `packer-templates` folder.

* Find the newest version number and checksum from http://releases.ubuntu.com/trusty/ and edit `PACKER_BOX_NAME` and `iso_checksum` in the template files to match.