
## 🍁Splunk SOAR (Phantom) : Home-Lab

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
        [![LinkedIn](https://img.shields.io/badge/LinkedIn-Profile-blue)](https://www.linkedin.com/in/nikhil--chaudhari/)
        [![Medium](https://img.shields.io/badge/Medium-Writeups-black)](https://medium.com/@nikhil-c)


## 🍁Introduction
In this Lab I will try to cover how can we install Splunk SOAR, and how we can configure it to play automation of threat response.

## 🍁What is SOAR ?
The SOAR stands for security orchestration, automation, and response. The SOAR platform provided by Splunk is known as Phantom. Earlier it used to have a different website but now has been integrated into the Splunk’s official website itself.

## 🍁Prerequisites
- Basic knowledge of command-line
- Familiar with Centos or RHEL operating system

## 🍁Requirements
- Requires centos 7 / RHEL 8 or later
- VMware or Virtualbox

## 🍁Install the Splunk SOAR
**Step 1**: Create a RHEL 8 machine with the user name phantom.

**Step 2**: During the installation of RHEL 8, on the UI while creating a user enter the user name and password but don’t give it administrative rights at the beginning.

**Step 3**: Install the splunk-soar-unpriv file.
ou can Download the unprivileged installer from “https://www.splunk.com/en_us/download/soar-free-trial.html?locale=en_us” after creating an account and starting the free trial.

You can directly copy the wget link and run it on the linux machine or follow **Step 3**.

![](https://github.com/DNcrypter/Splunk-SOAR-Phantom-Lab/blob/main/Images/img%201.jpeg)

**Step 4**: Go to directory where you downloaded splunk SOAR file. By default it is in Download directory.
```
cd Download
```
**Step 5**: Unzip the tar file.
```
tar -xzvf ./<splunk_soar_version>
```
Now wait for one or two minutes until it get unzip the file.

**Step 6**: Move uzipped file to /opt/soar/ path.
```
cp ./<splunk_soar_version> /opt/soar/
```
As we installed the RHEL and unzipped the unprivileged splunk soar package on our system.


## 🍁Configure the SOAR

**Step 1**: I used “chmod -R 777 /opt/” because it is a test environment and permissions are essential for unprivileged installation.

img 2:


**Step 2**: This step might be optional but if you have encountered a problem, you may need to disable SELinux.

img 3:

**Step 3**: Check firewalls daemon is running “systemctl status firewalld” . If the daemon is not running use the following commands:
```
sudo yum install firewalls
sudo systemctl start firewalls
sudo systemctl enable firewalld
```

img 4:

**Step 4**: Update operating system:
```
sudo yum clean all
```
```
sudo yum update
```

Login as a root and start the script using the following command for unprivileged installation.
```
./soar-prepare-system — splunk-soar-home /opt/soar/ — https-port 8443
```

img 5:

**Step 5**: In the script, it will ask for the creation of a user. give username and password.

which port will be used (default is 8443)?

**Step 6**: You can give “Y” for all options except cluster options. you can give different answers according to question asked.

img 6:

Give “n” this question.

img 7:

**Step 7**: This is an unprivileged installation, therefore switch the user that you were created during the installation phase. Note that, do NOT install SOAR as a root user.
```
./soar-install — splunk-soar-home /opt/soar — https-port 8443

```
img 8:

**Step 8**: You can Ignore errors and give “y”.

img 9:

At the end you will get completed installation message.

img 10:


**Step 9**: Start phantom services via “./start.phantom.sh”. Scripts are in the bin folder.

img 11:


**Step 10**: You can access the SOAR interface “localhost:8443”.

img 12:

```
username: Nikhil
password : password
```
## 🍁Conclusion
Now we have successfully installed and cofigured splunk SOAR. And we are ready to create playbooks and automate the system threats response.

If you like Project, follow me for such content.

