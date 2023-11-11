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
-