# How does it work?

When sending an e-mail, the mail has to be delivered to the recipients mail
server. For example: if you send an email to user@gmail.com, a connection is
made to one of Googles email servers to deliver the mail. An email sent to
user@live.com will be delivered to Microsoft.


All these mail senders have their own configuration. They may e.g. limit
the number of messages that may be delivered over a single connection,
how many connections may be opened from a single I.P. address. They may
also keep an eye on IP addresses that suddenly send a lot of mails when
they did not use to do so in the past and mark these mails as spam.

When using SMTPeter you don't have to worry about this at all. You simply
deliver your mail to SMTPeter and we take care of the rest. We make sure
to connect to the right server, and that the addresses we send from have
a reputation sufficient to avoid getting marked as spam. If the receiving
server can not handle the flow of messages, we throttle back delivery.

![](copernica-docs:SMTPeter/how_does_smtpeter_work_diagram.png)