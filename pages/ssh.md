- {{renderer :wordcount_}}
	- in the begining, before the internet had form, connections had to be made by hand
	- a basic technology that we still use today although is likely used by security people and sysadmins is telnet
	- telnet is a protocol that allows you to connect to a remote computer and interact with it using a command line interface
	- telnet is not secure, it sends all data in plain text and is not encrypted leading to a security risk
	- before SSH however, telnet was the only way to connect to a remote computer that was Unix based.
	- Windows had a similar protocol called RDP, but it was not as widely used as telnet back in the before times
	- Windows was not in existence until 1985, and it was not until 1993 that Windows NT was released, which was the first version of Windows that was based on the NT kernel (NT stands for New Technology, which still makes me laugh as we would say 'NT Technolgoies' in the 90s, which is like saying 'New Technology Technologies')
	- Much is said of recent about privacy, the privacy bill in the US, the GDPR in the EU, and the CCPA in California. In the UK, new privacy laws are being enacted that will threaten encryption where it is used to communicate over chat apps. This is due to the exponential increase of on line abuse, predatoral behaviour, and the use of encryption to hide these activities. So whilst some say that this threatens our privacy, it is understandable how this has come about.
	- Telnet was completely in the plain however and user names, passwords and any data passed beteen the operator and the server was in plain text and could be 'sniffed' by anyone with the right tools. Packet sniffing is a technique used by network engineers and black hat hackers alike to intercept data packets and read the contents. As with all things in technology, there is a good and a bad side to it.
	- SSH or 'secure shell' changed all of this. SSH was developed by Tatu Ylonen in 1995 and was designed to replace telnet. SSH is a protocol that allows you to connect to a remote computer and interact with it using a command line interface, but it does so in a secure way. SSH uses encryption to ensure that all data sent between the operator and the server is encrypted and cannot be read by anyone else.
	- SSH is a client server model, where the client is the operator and the server is the remote computer. The client and server both have a public and private key. The public key is shared with the other party and the private key is kept secret. When the client connects to the server, the server sends the client a random string of characters. The client then encrypts this string using the server's public key and sends it back to the server. The server then decrypts the string using its private key and if the string matches the original string, the client is authenticated and the connection is established.
	- there are two modes of operation for SSH, password and key based authentication. Password based authentication is the default mode and is the easiest to set up. Key based authentication is more secure and is the recommended mode of operation.
	- I, and many like me, use key based ssh authentication to connect to servers whenever possible and in preference to password based authentication. A key pair is stored securely and on the local machine and the public key is transferred to server(s). When we connect to a server, a random string is sent to the client, which is then encrypted using the private key and sent back to the server. The server then decrypts the string using the public key and if the string matches the original string, the client is authenticated and the connection is established.
	- To make life easier, ssh keys can be stored in a keychain, which is a secure storage area on the local machine. The keychain is encrypted and can only be accessed by the user. The keychain can be unlocked using a password, which is the same password that is used to log in to the local machine. The keychain is unlocked when the user logs in to the local machine and remains unlocked until the user logs out or the machine is shut down.
	- SSH does not only have to be used for interactive sessions where we type commands, get output back, type more commands and so forth where we may configure a server to do a thing, or just find out what it is doing and work out if we need to make further changes in an ad-hoc manner
	- We can also 'script' commands using ssh and run them on a remote server. This is useful for automating tasks that we may need to do on a regular basis, or for running commands on multiple servers at the same time.
	- this technique is taken to the next level by tools like Ansible which use this method of connecting to servers to run commands and scripts on multiple servers at the same time. Ansible is a tool that allows you to automate tasks on multiple servers at the same time. It uses SSH to connect to servers and run commands and scripts on them.
	- There is a vast community behind Ansible, a galaxy, you might say - https://galaxy.ansible.com - where you can find pre-written scripts that you can use to automate tasks on your servers. It would be safe to say I would think that without SSH, Ansible would not exist in its current form.
	- SSH has become so ubiquitous that other tools have been developed that use SSH to connect to servers and run commands and scripts on them. One such tool is Fabric, which is a Python library that allows you to automate tasks on multiple servers at the same time. Fabric is a Python library that allows you to automate tasks on multiple servers at the same time. It uses SSH to connect to servers and run commands and scripts on them.
	- rsync is a tool that allows you to copy files from one server to another. It uses SSH to connect to servers and copy files from one server to another. It is a very useful tool for backing up files from one server to another and forms the backbone of many backup solutions.
	- sshfs is a tool that allows you to mount a remote filesystem on your local machine. It uses SSH to connect to servers and mount a remote filesystem on your local machine. It is a very useful tool for accessing files on a remote server and is often used by developers to access files on a remote server, such as a web server, although it is best suited to Linux environments but there are Windows versions available https://github.com/winfsp/sshfs-win.
	- Of old, Microsoft actively discouraged any kind of integration with Windows post to NT3.51 and NT4.0, and it was not until Windows 2000 that Microsoft started to again embrace the Unix world. Since these dark days of the 90s, Microsoft has embraced the open source world and has even released its own version of Linux, Azure Sphere, which is a Linux distribution that runs on the Azure cloud platform. SSH is supported in Windows 10 and Windows Server 2019, and there are many tools available for Windows that use SSH to connect to servers and run commands and scripts on them. Mac OS X has had SSH support since version 10.0, and there are many tools available for Mac OS X that use SSH to connect to servers and run commands and scripts on them. If you live in the Mac world, basically, you've been using SSH for a long time, if you ever open a terminal window and type ssh that is, you are using SSH.
	- I've had security people ( of which I count myself by the way ) but some over time thought SSH in some way insecure and favour Windows RDP. This in my thinkng was a kind of madness but I think it had its origins in security managers being primarily Windows based in some of these environments. This is ironic as every hacker I've come across, black hat and whites alike, use SSH Unix operating systems and SSH routinely, some even see Windows as entirely insecure as compared to hardened Linux distributions.
	- Suffice to say, ssh can be hacked and I've seen this happen, but this has usually been caused by wrong configuration of the ssh server, or the use of weak passwords. SSH is not a silver bullet, but it is a very useful tool that can be used to connect to servers and run commands and scripts on them. It is a very useful tool for automating tasks on multiple servers at the same time. It is a very useful tool for backing up files from one server to another.
	- Some ways to 'harden' ssh are to use key based authentication, disable password based authentication, disable root login, and use a firewall to restrict access to the ssh port. The port on which SSH is configured to run, port 22 can be changed to another port, so long as you know what your doing and don't lock yourself out of the server. When using ssh to reconnect to a server runing on say, port 9876, you would use the following command: ssh -p 9876 user@server. To sftp ( secure ftp ) to a server running on port 9876, you would use the following command: sftp -P 9876 user@server, or `-oPort=9876` if you are using the OpenSSH client. Another thing that can be done is to configure tools to check for ssh being hacked, such as fail2ban, which is a tool that monitors log files for failed login attempts and blocks the IP address of the attacker. Fail2ban can be configured to insert firewall rules to block attackers, and can also be configured to send email alerts when an attack is detected.
	- Other tools can be used to harden SSH, it may be put entirely behind a secure VPN for example, or a bastion host, or a jump box, or a combination of these.
	- Azure has a service called Azure Bastion, another option for fronting your infrastructure access with a secure service.
	- Teleport is another option, which is a tool that allows you to connect to servers and run commands and scripts on them. It has a hosted version, which is free for up to 5 users, and a self hosted version, which is free for up to 5 users. It is a very useful tool for automating tasks on multiple servers at the same time.
	- TailScale is another option, which is a tool that allows you to connect to servers and run commands and scripts on them. It has a hosted version, which is free for up to 5 users, and a self hosted version, which is free for up to 5 users. A self hosted version called Headscale which you can host yourself, using tailscale client technology, which is also open source.
- {{renderer :wordcount_}}
	- ssh can be used to extend our reach to other servers in order to access services that are running on remote endpoints, as if they were hosted locally. This is done using a technique called 'tunnelling' where we create a tunnel between our local machine and a remote server. This tunnel allows us to access services that are running on the remote server as if they were running on our local machine. SSH can be made to achieve this with something like the following 
		- ```bash
		ssh -N -R <local-port>:localhost:<remote-port> <user>@<remote-server>
		```
		where `<local-port>` is the port on our local machine that we want to use to access the service, `<remote-port>` is the port on the remote server that the service is running on, `<user>` is the user that we want to connect as, and `<remote-server>` is the remote server that we want to connect to.
		-R is the option that tells ssh to create a reverse tunnel, which is a tunnel that allows us to access services that are running on the remote server as if they were running on our local machine.
		-N is the option that tells ssh not to execute a remote command, which is the default behaviour of ssh when connecting to a remote server.

		and here is an example of how this might be used to access a remote servers database, running MySQL on port 3306, from our local machine on port 3306:
		```bash
		ssh -N -R 3306:localhost:3306 username@remote-server

		``` 
		- this would allow us to connect to the remote servers database from our local machine using the following command:
		```bash
		mysql -h localhost -P 3306 -u username -p
		```
	- So by running one or more ssh commands on a local system, we can connect that remote servers and access their services as if they were local.
	- another common use of ssh is to access things like a web service that is behind a trusted host. Sometimes this is called a 'bastion' or 'jump server'. This is a common scenario where services and hosts are running on networks that are not available to external connections. This is a common practice in many organisations where there is a need to access services that are running on internal networks from external networks. 
		- a connection to the bastion host is established
		```bash
		ssh -L <local-port>:<web-server>:<web-service-port> <bastion-user>@<bastion-host>
		```
		where <local-port> is a local port on our local machine
		<web-server>: The internal IP address or hostname of the web server.
		<web-service-port>: The port on which the web service is running on the web server.
		<bastion-user>: Your username on the bastion host.
		<bastion-host>: The IP address or hostname of the bastion host.
		for example
		```bash
		ssh -L 8080:web-server:80 bastion-user@bastion-host
		```
		- next dynamic port forwarding is used to create a SOCKS proxy on our local machine
		```bash
		ssh -D <local-socks-port> <bastion-user>@<bastion-host>
		``` 
		where <local-socks-port> is a local port on our local machine
		
		Now, you can access the web service by opening your web browser and navigating to http://localhost:<local-port>. The traffic will be tunneled through the bastion host to the web server.

	- another use of ssh is to, with a single ssh command, jump through a bastion server to access one that is running behind it, using the the ProxyJump or -J option in the ssh command to connect to a host that is behind a bastion host. Here's the syntax:
	```bash
	ssh -J <bastion-user>@<bastion-host>:<bastion-port> <target-user>@<target-host>:<target-port>
	```
	<bastion-user>: Your username on the bastion host.
	<bastion-host>: The IP address or hostname of the bastion host.
	<bastion-port>: The SSH port on the bastion host (usually 22).
	<target-user>: Your username on the target host.
	<target-host>: The IP address or hostname of the target host.
	<target-port>: The SSH port on the target host (usually 22).
	-J is the option that tells ssh to connect to a host that is behind a bastion host.
	for example
	```bash
	ssh -J bastion-user@bastion-host:22 target-user@target-host:22
	```
	Alternatively, you can use the older syntax without the -J option:

	```bash
	ssh -o "ProxyJump=<bastion-user>@<bastion-host>:<bastion-port>" <target-user>@<target-host>:<target-port>
	```
	but it is more common practice to store this in your ssh config file, which is located at ~/.ssh/config on Linux and Mac OS X, and %USERPROFILE%\.ssh\config on Windows. Here is an example of how this might look:
	```bash
	Host target-host
    HostName <target-host>
    User <target-user>
    Port <target-port>
    ProxyJump <bastion-user>@<bastion-host>:<bastion-port>
	```
	then, to access the remote server using the bastion host, you would use the following command:
	```bash
	ssh target-host
	```
	Both configurations achieve the same result: tunneling through the bastion host to connect to the target host. Save the changes to your ~/.ssh/config file, and then you can use the simplified ssh target-host command.
	- so there are many use cases for ssh and it has many more, not yet discussed here but it is possible to use just SSH to manage remote hosts securey over secure, public private key encryption without VPNs or other proprietary services
	- SSH itslelf can be hardened or itself accessed using VPN solutions in ways that reduce attack serfaces and increase security whilst still allowing remote access to remote hosts with relative ease
	- what started out with telnet, a useable but insecure method for modern day use cases, SSH has mostly replaced this with a secure, encrypted method of connecting to remote hosts and running commands and scripts on them and many more applications, amounting to a swiss army knife of remote access and management
	- for years, there was resistence to SSH in Windows. Now, this is entirely gone and SSH is supported within modern Windows, indeed WSL, ( Windows Subsystem for Linux ) a virtual machine that runs Linux on Windows, is commonly used by developers to have their own Linux distribution running locally along side windows. This is in my view, the easiest way for anyone to run Linux aside of running linux on a separate host, and is a great way to learn Linux and get to know the command line. With this, SSH is not as alien to Windows users as it once was, and is now a common tool for Windows users to use to connect to remote servers and run commands and scripts on them, whilst windows shell itself now supports SSH, and there are many tools available for Windows that use SSH to connect to servers and run commands and scripts on them.
	- the popular editor and IDE, Visual Studio Code has many plugins, VSCode itselft being open source and written by Microsoft teams, several of which integrate SSH into the editor, allowing you to connect to remote servers and run commands and scripts on them. More so, when using this plugin to connect to remote servers, VSCode continues to work on the remote server, installing a proxy on that server and allowing you to use VSCode as if it were running locally. This is a great way to work on remote servers. Even plugins that you would use locally can be used on the remote server, such as the Python plugin, which allows you to run Python code on the remote server and see the output in the editor, as if it were running locally and with lint checking, debugging and other features that you would expect from a modern IDE when running code locally.
	- it is fair to say that MacOSX has increased in popularity in the development community at least in part due to poor integration with the Unix ecosystem and it would have been for this reason alone that, given a choice, I would have become an Apple user over that of being a captive Windows user. But in the real world of work, where IT departments are run by corporations that are already Micrsoft shops