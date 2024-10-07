# SSH you never know who's listening

So this is just a run down on how ssh works which really can be very high level as the lower level cryto stuff can be taken care of when chatting about crypto101.

As part of this just chat about ssh agent and ssh add how that all works.

For setting up SSH login for my github I can just update the ssh config so that for the domain github.com it points towards a particular key.

There are more advanced benefits of using and agent although it is mostly for using password protected keys I think.

Ssh - you never know who’s listening
Secure shell was set up to provide a secure means of connecting to a remote server over the internet.
At a high level it all seems pretty straightforward to be honest.
But before we get into that there are actually a couple of dependencies that I would like to look into in a little more detail.
First amongst these is the requirement for a connection protocol to enable the communication to occur in any fashion. For the purposes of this article I will focus on the Transmission Control Protocol although it is also possible to conduct this over a Web Sockets connection for example although I don’t know how that workds at all. It could take place over the likes of a UDP connection which is a “best effort” connection as per cloudflare docs.
So what is a TCP connection and how does it work.

You use TLS every day when you surf the web or use a smartphone app. It's the most common form of encryption on the Internet. HTTPS uses TLS for encryption.

TLS sits over TCP which is a good note to have. 
TCP ensures reliable transmission of packets which is essential for SSH.
The three way handshake needs to take place for this connection to be established. 
The steps are as follows:~

On top of the encryption functionality SSH allows you to provide commands to be run on a remote server.
You require applcation layer protocol such as http to run on top of TLS
SSH is at the application layer.

Cool that’s probably enough at the connection level as it can run over TCP

I’ll probably do a debrief at some stage on the different connection level protocols such as TCP, UDP and WebSockets if that is an appropriate application.
Ok another dependency is encryption though and this time its on the encryption side of things.

Symmetric encryption is actually used for a lot of SSH informtion it is only in the initial authenticatin stage that asymmetric encryption is used so that the symmetric key can be shared between the two.

Encrypt a message with their public key and your private key  so that only they can read the message and they know that it has come from you.

Digital ocean article was just brilliant really and here is another great quote from it
The more well-discussed use of asymmetrical encryption with SSH comes from SSH key-based authentication. SSH key pairs can be used to authenticate a client to a server. The client creates a key pair and then uploads the public key to any remote server it wishes to access. This is placed in a file called authorized_keys within the ~/.ssh directory in the user account’s home directory on the remote server.

Important
Authenticating user access to the server.
We have set up an encrypted connection which has used asymmeteric to share a shared secret. Then you could provide the password to authenticate although this isn’t actually the recommended method due to limitations on password structure.

Authentication using SSH key pairs begins after the symmetric encryption has been established as described in the previous section.

Then it’s pretty simple but there is one other caveat that was missing from the initial digital ocean article but was in the second one and that is
For this method to work, you must currently have password-based SSH access to your server.
So you will need to do password based initailly to add the key pair to authorized keys.
Then after that your good to go so the password enabled method is only needed to be used once to get the file there.
Note:
-	What is the known hosts directory in ssh
-	https://csrc.nist.gov/glossary/term/known_hosts_file#
Probably need to chat quick about the challenge upon connection to authenticate.


