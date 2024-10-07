for this one need to firstly read the crypto101 pdf from the guy at pycon and then distill the highlights into this note.

took this after wondering what the difference between a password and a symmetric API key is

Access tokens (in most services) can be easily generated, blocked, monitored for their usage & statistics from your account, can be set as expirable, can have restricted permissions, and so on... Of course, you can delete it at all. The Username & Password is the master, who can control the access tokens.
Access tokens are safer as I said, and that is the most important thing. If you use Username & password in your web-application (or whatever) and that application is hacked (which happens so frequently), or someone views its source, or even some log-system saves the request parameters - then your user & password can be viewed by 3-rd parties and all your account can be hacked (and probably others too, where you have same user/pw). Access tokens eliminate all these risks.
https://stackoverflow.com/questions/53919956/access-token-vs-username-password-for-api-request
