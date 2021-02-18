# nullmailer Rewrite Wrapper: Force a fixed from address and redirect mails to local users
This littler wrapper script is intended to rewrite all mails to user specified from address. 
In addition a central address is provided where all mails for local users go to. This prevents that mails that are intented for you/root go to the wrong person, but instead to your defined email address.

## Benefits or nullmailer Rewrite Wrapper for nullmailer privacy
Without rewriting the from address to that of your mailaccount your local username and hostname is exposed to the receiver, like `X-Google-Original-From: <root@raspberrypi>`

With rewriting E-Mail will appear as truly send from like MailSenderUser1234@gmail.com

Please also set `/etc/nullmailer/idhost` to something like `nullhost` otherwise your hostname will be exposed in `Message-ID` header-field.

Please also set `/etc/nullmailer/helohost` to something like `nullhost` otherwise your hostname will be exposed in `Received: from` header.

## Installation instructions
Execute as root (if applicable change the paths):

`cd /usr/sbin`

`mv sendmail sendmail-bin`

copy sendmail from this repository to /usr/sbin/sendmail 
edit the copied sendmail file at these lines: 

`export NULLMAILER_USER=yourmailaddress` e.g. MailSenderUser1234

`export NULLMAILER_HOST=yourMailDomain` e.g. gmail.com

`Admin_Address=yourMailAdress@yourMailDomain.com` Where should mails go that are directed for local users like "root" or "pi" e.g. MailSenderUser1234@gmail.com or alertqueue@example.net This address is idependent of sender address

`chmod --reference=sendmail-bin sendmail` to prevent normal users to make changes and intercept all mail from this host

### Configure Nullmailer

Please set 
`/etc/nullmailer/adminaddr` to your admin-address. If some program sends to "<user>@<hostname>" e.g. "root@mysuperhost" or "blabla@localhost" this address is rewritten by nullmailer. 

If it is only send to "root" or "pi" like some programs do, then it is rewritten by this script. For maximum complexity disregarding KISS principle these both addresses could differ.

