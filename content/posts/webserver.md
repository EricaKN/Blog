---
title: "You can use it, but can you make it? DIY your own web-server"
date: 2024-08-30T07:53:12-03:00
draft: false
<!-- draft: false --> 
<!-- image: images/sshlogo2.png -->
tags: ["web-server"]

---
# Goal
---
Let's create a TCP/IP packets to enable a client-server 

---
# Installing Golang
---
## OpenBSD
---

``` console
doas pkg_add go
``` 

``` console
go version
``` 



ubuntu
https://www.digitalocean.com/community/tutorials/how-to-install-go-on-ubuntu-20-04

curl -OL https://golang.org/dl/go1.16.7.linux-amd64.tar.gz
Then use curl to retrieve the tarball, making sure to replace the highlighted
URL with the one you just copied. The -O flag ensures that this outputs to a
file, and the L flag instructs HTTPS redirects, since this link was taken from
the Go website and will redirect here before the file downloads:


To verify the integrity of the file you downloaded, run the sha256sum command
and pass it to the filename as an argument:

sha256sum go1.16.7.linux-amd64.tar.gz

If the checksum matches the one listed on the downloads page, you’ve done this step correctly.

Next, use tar to extract the tarball. This command includes the -C flag which
instructs tar to change to the given directory before performing any other
operations. This means that the extracted files will be written to the
/usr/local/ directory, the recommended location for installing Go… The x flag
tells tar to extract, v tells it we want verbose output (a listing of the files
being extracted), and f tells it we’ll specify a filename:
sudo tar -C /usr/local -xvf go1.16.7.linux-amd64.tar.gz


In this step, you will set paths in your environment.

First, set Go’s root value, which tells Go where to look for its files. You can do this by editing the .profile file, which contains a list of commands that the system runs every time you log in.

Use your preferred editor to open .profile, which is stored in your user’s home
directory. Here, we’ll use nano:

sudo nano ~/.profile

Then, add the following information to the end of your file:
export PATH=$PATH:/usr/local/go/bin

After you’ve added this information to your profile, save and close the file. If you used nano, do so by pressing CTRL+X, then Y, and then ENTER.

Next, refresh your profile by running the following command:

---
# Web-server architecture
---

## ssh


## Directories

``` console
mkdir go_webserver
```
|-- go_webserver
|   |-- server.go



## Files
### server.go



# References
---
https://www.digitalocean.com/community/tutorials/how-to-install-go-on-ubuntu-20-04




https://medium.com/@sharmaadityaf723/creating-a-web-server-with-golang-25cd57d6fb58

