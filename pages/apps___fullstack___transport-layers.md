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
		- TODO : how to send emails from a web app, could be SMTP to an existing provider that accepts SMTP over TLS, or could be using an API like sendgrid
		- So, having sent an email, how do we recieve one, and in a programmatic way ?
		- there are solutions out there like IFFT, Zapier, Microsoft Flow, and some have free tiers that allow you to do some basic processing of incoming emails
	- in order to stay true to the origonal idea of keeping it simple and so as to have a reasonale amount of control over the process, we will use a nodejs script to recieve and process the email, then these other servicves can be used at a later time if needed but in the mean time, we have a working solution that is visible and easily understood. It also involves as few third parties as possible, at least for now
	- here is an example block of javascript that will recieve an email and process it :
		- ```javascript
		  // read config from .env file
		  require('dotenv').config();
		  // read POBOX from .env file
		  const USER = process.env.USERACCOUNT;
		  const PASSWORD = process.env.PASSWORD;
		  const SERVER = process.env.SERVER;
		  const PORT = process.env.PORT;
		  
		  // console.log(USER, PASSWORD, SERVER, PORT);
		  
		  
		  const Imap = require('imap');
		  const { simpleParser } = require('mailparser');
		  const imapConfig = {
		  user: USER,
		  password: PASSWORD,
		  host: SERVER,
		  port: PORT,
		  tls: true,
		  };
		  
		  const getEmails = () => {
		  try {
		  	const imap = new Imap(imapConfig);
		  	imap.once('ready', () => {
		  		imap.openBox('INBOX', false, () => {
		  			imap.search(['UNSEEN', ['SINCE', new Date()]], (err, results) => {
		  				if (!results.length) {
		  					console.log('No new unseen emails.');
		  					imap.end(); // Close the connection
		  
		  					return;
		  				}
		  				const f = imap.fetch(results, { bodies: '' });
		  				f.on('message', msg => {
		  					msg.on('body', stream => {
		  						simpleParser(stream, async (err, parsed) => {
		  							const {from, subject, textAsHtml, text} = parsed;
		  							console.log('From: ', from);
		  							console.log('Subject: ', subject);
		  							console.log('Text: ', text);
		  
		  							// console.log(parsed);
		  							/* Make API call to save the data
		  							Save the retrieved data into a database.
		  							E.t.c
		  							*/
		  						});
		  					});
		  					msg.once('attributes', attrs => {
		  						const { uid } = attrs;
		  						imap.addFlags(uid, ['\\Seen'], () => {
		  							// Mark the email as read after reading it
		  							console.log('Marked as read!');
		  						});
		  					});
		  				});
		  				f.once('error', ex => {
		  					console.log('Fetch error: ' + ex);
		  					return Promise.reject(ex);
		  				});
		  				f.once('end', () => {
		  					console.log('Done fetching all messages!');
		  					imap.end();
		  				});
		  			});
		  		});
		  	});
		  
		  	imap.once('error', err => {
		  		console.log('message of error is ...')
		  		console.log(err.message);
		  	});
		  
		  	imap.once('end', () => {
		  		console.log('Connection ended');
		  	});
		  
		  	imap.connect();
		  } catch (ex) {
		  	console.log('an error occurred');
		  }
		  };
		  
		  getEmails();
		  
		  
		  ```
		- and there is a sample output of an email I sent to the account that this script is configured to read from :
		- ```bash
		  Subject:  more data and stuff
		  Text:  1a23 buckle my shew
		  
		  Marked as read!
		  Done fetching all messages!
		  ```
		- for simplicies sake I have not made any effort to structure the data, but that is a simple matter of parsing the text and then saving it to a database or whatever
		- an application of something similar to this was where I used this to test for the availability of an email servivce, such that, at any point in time up to 10 minutes ago, the ISPs support team are able to look at a web page with a dashboard and to see that the email service has been able to have mail sent to it, through SMTP and mails are recieved from it over IMAP or POP3, which ever is configured by their users at that time.
		- what was once a slew of daily issues with clients ringing up the support desk with complaints of email not working were reduced to only a few as the support team could eliminate this as a cause and rather, diagnose the issue as being with the clients email client or their internet connection or their computer or whatever, providing a better, more efficient service to the clients and reducing the stress on the support team
		- so we have a transport. All I wanted to show in this is that something that predates the web in its current form and based upon html and web pages, can still be used as a means of programatially sending and recieving data, and that it is not that difficult to do so.
		- Webcheck, a tool I helped develop starting before Y2K used email or rather SMTP and POP3 as its transport mechanisms in addition to http and https to serve data connections. We later introduded SOAP as an additional layer for management between core funcdtions but to gather statistical data, SMTP was at its core
		- This solution was not alone in this use case and others I came across used much the same approach to gather data from many franchise operations across the UK and throughout Europe and further afield. Performance data was sent by each franchise server using email SMPT transport to do so. Its data packets were serialised as the mail body and services at the recieving mail boxes decoded these and stored them in a database for later analysis and reporting. The internet as we know it now was very much in full swing and this method was still being used to gather data from remote locations and to send it to a central location for analysis and reporting. It was a simple, effective and reliable solution.
		- If you think about it, using a mail box to recieve data and to process it off line so to speak is little diffent in principle to a queue. Indeed a part of managing email at scale is to manage email queus, within the email service itself. Often email transports are not just recieving and sending all the time, rather they are ingressing emails to pipeline them into a series of operations responsible for routing, filtering, checking for spam, malware and so forth. Some queues are thus for quarantine and others for delivery and so on.
		- Transports for data are more often than not now migrated to use queue technologies and their ingress are often fronted by APIs that are RESTful in nature, permitting for the scaling of the ingress and egress of data to be managed in a more granular way. This is not to say that email is not used as a transport, it is, but it is not the only one and it is not the only one that is used to send and recieve data. It is however, one of the oldest and most reliable and it is still used to this day, even if it is not the only one.
- remember to add story about managers against SMTP
- {{renderer :wordcount_}}
	- ehreer