# VM for Udemy cours "Node JS : Advanced Concepts"

## WHY ?

The version of NodeJS used in this course is a bit dated (V12). This is deprecated and not recommended for installation, but the code used works with it, which is not the case with more recent versions (v14+). To avoid modifying local installations and for those who don't use NVM, here is a VagrantFile that can be used to take the course.

## Required Configuration

* Oracle Virtualbox version 6.1.28 or +
* vagrant version 2.x
  > **Make sure you have the id_rsa.pub and id_rsa files in the *C:\Users\\%UserName%\\.ssh* folder on Windows, or *~/.ssh* folder on MacOs/Linux OS.**
* CPU *4cores/8threads* and *6GB RAM* **minimum**.
  > **If your configuration is less powerful, you can modify this line to adapt according to your computer:**<br>
  >>```vb.cpus = 4```<br>
  ```vb.memory = "4096"```<br>

## Installation

At the root of the folder where the VagrantFile is located, in a terminal or console, run `vagrant up`.

## Use

After installation, at the root of the folder where the VagrantFile is located, in a terminal or console, run `vagrant ssh` to connect to the guest.
Run the following commands to start the NodeJS server: 
```shell
vagrant@bullseye:~$ cd /var/www/AdvancedNodeStarter && npm run dev
```
> **Make sure you have changed the information found in the ***/var/www/AdvancedNodeStarter/config/dev.js*** file in the guest beforehand (*see the course*).**

From the host, open a browser and go to http://localhost:8080.
> **You can change port 8080 to whatever you want at this line:**
>>`config.vm.network "forwarded_port", guest: 3000, host: `***8080***` `

> **You can also change the IP address (localhost/127.0.0.1) to whatever you want, like this:**
>>`config.vm.network "forwarded_port", guest: 3000, host: 8080, `***host_ip: 127.0.0.2***` `

#### *For more information:*

[Vagrant documentation](https://www.vagrantup.com/docs/networking/forwarded_ports)


## *Useful links*

* [Oracle VirtualBox](https://www.virtualbox.org/) *(free)*
* [Vagrant](https://www.vagrantup.com/downloads) *(free)*
* [Create a SSH Key on Windows](https://docs.microsoft.com/fr-fr/windows-hardware/manufacture/desktop/factoryos/connect-using-ssh?view=windows-11#create-a-keypair) *(documentation)*
* [The course on Udemy](https://www.udemy.com/course/advanced-node-for-developers/) *(requires an account and course purchase)*