- {{renderer :wordcount_}}
	- email is a transport layer and one which has been used quite literally since the dawn of the internet
	- it is based on the simple idea of sending a message from one place to another and uses a protocol called SMTP
	- SMTP stands for Simple Mail Transfer Protocol
	- you can send from the command line with the command `mail`
	- for example
		- `echo "This is the body of the email" | mailx -s "Subject of the email" person@mail.example.com`
	- you can also send from the command line with the command `sendmail`
	- first we creat a text file that has the body of the email in it
		- ```bash
		  To: person@mail.example.com
		  Subject: Your subject here
		  
		  This is the body of the email.
		  
		  ```
	- then we can send it using sendmail
		- `sendmail -t < email.txt`
	- to programmatically process an incoming email we could
	- **Create a Script:**
	  Create a script or program that will process the incoming email. This script could be written in any scripting or programming language you are comfortable with, such as Bash, Python, Perl, etc. The script should read the email content from standard input (stdin) or from a file.
	- Example script (`process_email.sh` in Bash):
	- ```bash
	  #!/bin/bash
	  while read line; do
	  # Process each line of the email
	    echo "Processing line: $line"
	  done
	  ```
- then in our unix account we add a `.forward` file containing something like
	- `"|/path/to/your/script.sh"`
- this was fine when we were building our own email servers and email transports using sendmail, exim, postfix et. al. but thanks to the spam kings out there, running an email server is left to the expert, well established and recognised providers, be they microsoft with outlook, yahoo
- Only thing is, who has a Unix account on a server that is configure to recieve email locally these days ?