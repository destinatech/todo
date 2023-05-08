# / INFRA / PROVISIONING / ORACLE CLOUD

## OC Compute -- Instance Set-up

Perform the following tasks once the instance has been created and is online:

1.  **Log in to Oracle Cloud and restrict SSH access to home IP only**

- Create Network Security Group (NSG) named `ssh-access`

- Specify source address as home IP and destination port as `TCP/22`

- On the "instance details" page for the instance, click "Edit" next to
  "Network Security Groups" and select the newly-created `ssh-access` NSG

- Verify that all ports are filtered with an online scanning tool
  (e.g. <https://hackertarget.com/nmap-online-port-scanner/>)

- Finally, go to the default security list for the VCN the instance is on and,
  if not already removed, delete the rule which allows SSH access from
  everywhere

2.  **SSH into the system and run**

```
# apt update && apt dist-upgrade
# reboot
```

3. **Replace default ubuntu/ubuntu user/group**

```
# groupmod -n dtadm ubuntu
# userdel -fr ubuntu
# useradd -d /home/dtadm -g dtadm -m -s /bin/bash -u 1001 dtadm
# mkdir -m0700 ~dtadm/.ssh && chown -R dtadm:dtadm ~dtadm
# cp ~/.ssh/authorized_keys ~dtadm/.ssh/ && chown dtadm:dtadm ~dtadm/.ssh/authorized_keys
# gpasswd -a dtadm sudo
# passwd dtadm
```

4.  **Configure sudo**

Enable `pwfeedback`  option (prints asterisks when typing password):

```
	# cp /etc/sudoers{,.dist}
	# sed -i -e 's/^Defaults.*env_reset$/Defaults        env_reset,pwfeedback/' /etc/sudoers
```
To verify with diff run:

```
# diff -Nup /etc/sudoers{.dist,}
--- /etc/sudoers.dist   2023-05-08 08:45:40.775576518 +0000
+++ /etc/sudoers        2023-05-08 08:45:46.599617423 +0000
@@ -6,7 +6,7 @@
 #
 # See the man page for details on how to write a sudoers file.
 #
-Defaults        env_reset
+Defaults        env_reset,pwfeedback
 Defaults       mail_badpass
 Defaults       secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
 Defaults       use_pty

```

<!--
vim: ts=2 sw=2 et fdm=marker :
-->
