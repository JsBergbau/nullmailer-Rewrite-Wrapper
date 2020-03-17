# nullmailer Rewrite Wrapper
This littler wrapper script is intended to rewrite all mails to user specified from adress. 
In addition a central address is provided where all mails for local users to to. This prevents that mails that are intented for you/root go to the wrong person, but instead to your defined email address. 

## Installation instructions
Execute as root (if applicable change the paths):

`cd /usr/sbin`

`mv sendmail sendmail-bin`

copy sendmail from this repository to /usr/sbin/sendmail 
edit 

`export NULLMAILER_USER=yourmailaddress` e.g. MailSenderUser1234

`export NULLMAILER_HOST=yourMailDomain` e.g. gmail.com

`Admin_Address=yourMailAdress@yourMailDomain.com` eg. user1234@gmail.com

`chmod --reference=sendmail-bin sendmail` to prevent normal users to make changes and intercept all mail from this host

### Configure Nullmailer

Please set 
`/etc/nullmailer/adminaddr` to your admin-address. If some program sends to "<user>@<hostname>" e.g. "root@mysuperhost" or "blabla@localhost" this address is rewritten by nullmailer. 
Set `/etc/mailname` to your hostname

