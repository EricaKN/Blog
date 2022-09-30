---
title: "How to access a server using SSH-keys"
date: 2022-09-30T07:53:12-03:00
draft: true
---

# Pre-requisites
--- 

On this post, we are going to configure and access a server using SSH on:
 - Ubuntu 22.04 Linux machine

---
# Context
---

During my first professional experience as a Data Scientist/ Engineer, I was responsible for a CNN (Convolutional Neural Network) model that predicts if the Electrocardiogram Exams (yes! It is that kind of heart-exam that children use to draw, with a continuous line!) presents a time-sensitive health condition, and if the patient needs to be prioritized for a doctor.

I had to deal with hundred of thousands images and my notebook's graphic card was not able to deal with this amount of data. 

That's why I had to use SSH to access and run the model in the company CDP server, which was (of course) much more powerful than my notebook, and on this post I will show you how to configure and access a server using SSH.

---
# Commands to use on the:
---

## Server:
---

- Update package informations from all configured sources:

```console
sudo apt update
``` 

- Install OpenSSH Server packages ("connectivity tool for remote login with the SSH protocol", source: https://www.openssh.com/)

```console
sudo apt install openssh-server
```

- Initialize SSH using systemctl (https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units) 

```console
sudo systemctl start ssh
```

- [Optional] If you want to avoid being logged out of the system if it is rebooted, you may want to enable the service to start at boot (https://documentation.suse.com/smart/linux/html/reference-systemctl-enable-disable-services/index.html#:~:text=systemctl%20is%20the%20systemd%20command,it%20will%20start%20at%20boot.)

```console
sudo systemctl enable ssh
```

- Check the status of the service

```console
systemctl status ssh
```

- Get the IP address of the server (it will probably start with: "192.168.200...")

```console
ip address
```


---
## Workstation
---

- Generate a SSH-keys on your workstation. The keys function are similar to passwords, but "keys are not human generated, and unlike passwords, your private SSH key isn't sent to the server. So even if malicious actors hack into the server, they still can't access your account" (sourice: https://thorntech.com/passwords-vs-ssh/#:~:text=Additionally%2C%20SSH%20keys%20aren't,can't%20access%20your%20account.) 

```console
ssh-keygen
```

- Check if your network connectivity works

```console
ping -c 3 <ip_address_of_your_server>
```

- Once you have your network connectivity active, install the SSH key as an authorized key on the server

```console
ssh-copy-id <remote_usr_account>@<IP_address>
```

- Test SSH connectivity

```console
ssh <remote_usr_account>@<IP_address>
```

# Conclusion and correlated posts
That is how we can configure and access a remote server using SSH-keys. 
In the following posts I will show you other important tools to run your model remotely, e.g.:
- VSCode extension: Remote - SSH,
- tmux.

See you then!
