June 20

Was introduced to Turbo within Rails today which was the reason that my vanilla js was disappearing or being removed upon a re render of the application by the component library

June 22

was struggling with the communication of emit and refs. Had been trying to emit a new object to an array which was in the parent component. Solved this by using global state which was shared across components. This did highlight to me though the reasoning why the contents of a ref need to have the value property associated with it. (link to why use refs in my Vue documentation). Essentially it enables Vue to track what needs to be re rendered as this would not be possible with a basic JavaScript variable. Also when a non-primitive structure such as an array or object is wrapped inside a ref it invokes the reactive hook which converts this into a [Proxy object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy) which is something a little different as linked to on the Mozilla docs.

June 23

Was working on the Pivotal Kanban board with Richard and had some struggles with the DOM lifecycle using Vue so definitely need to look into that. Also highlighted the inefficiency of my developer workflow seeing how Richard and Gus are able to navigate so I will be looking to implement Jake Zimmerman’s [**Vim as an IDE](https://blog.jez.io/vim-as-an-ide/)** in the next little while. Update: I think there is some stuff out there on how like the virtual DOM works and all that jazz. In fact there are honeypot documentaries on both Vue and React 

June 29

Been on a project all day today and yesterday which has required a lot of concentration, and some struggles, but it’s been good. I’ve been learning/struggling with associations for a little while. Routing and nested routing has also been a new learning. Just getting to grips with that a little bit. Parameters and how they interact with the controller and the request has also been something which is gradually starting to make some more sense and that it is a special object which is essentially a hash where these parameters are somewhat automatically associated with controllers in a has many relationship so that you can identify a particular and all that jazz. FactoryBot and traits was also a bit of a struggle and getting to grips with how all of that works. Then also it was my first time kind of working with haml over erb (not really sure if I see the benefit as of yet) nearly find it a little more confusing if anything.

July 3rd

Struggling with importing bootstrap into a pre existing application. Was coming across sprockets as a key entry point in this workflow and it seems like its a whole thing. It kind of looks like sprockets like comes by default with newer versions of rails but definitely need to read up on the asset processing timeline to understand this more clearly. TO DO: After the fact update here but would be good to look at the asset pipeline.

July 10

Git rebase - need to learn a lot more about the inner workings of git rebase

Note: getting back to this on August 10th and feel like I have better understanding at this point. each commit on the branch that you are rebasing is sequentially added on to the branch you are rebasing onto. if there are lots of back and forward you would have to resolve conflicts one by one. have to git push force after rebasing as it is a destructive command that rewrites the history

- also may be worth mentioning like best practice of git rebase merge as opposed to straight up merge which would create a merge commit
- also probably better to squash commits down to meaningful commits
    - this could be where it could be useful to do like interactive squash - there may be another term for this I’m not really sure

July 26

Really struggling to implement BEM for styling frontend components using SCSS.

Have gotten my head around SCSS which is fairly straightforward and is pretty well just basic CSS which is just prioritised in order of import

BEM introduces structure and hierarchy to this then but can figure out what the behaviour is if you apply the styling of an element without having a parent element referencing the block

August 4th

It was a struggle to synchronise system wide gems and local gems which were installed using bundle install. Bundle install installs the gems locally and it should also override things. But this can get complicated if you are also using like rbenv to control the ruby version which is being used. In my case I wanted rubocop to use the bundled setup which was installed using bundle install. However you need to specify this by using bundle exec rubocop to be used for linting. This is a setting for the vscode plugin of rubocop to useBundler. I had been overriding this on save to point to the location of the system wide binary which meant that when this tried to run it did not have all the dependent gem files. In order for it to use the

August 10th

Using Administrate Ransack gem which was helping to implement filtering in rails. However while doing this I came across the struggle of how the selections on the form and their labels from within the html are converted into query parameters. This is something that I think could be worth looking at as to how a url is constructed and how query parameters work and all that jazz. There is also the somewhat interesting concept of how symbols like brackets and all that are encoded to other characters and why that happens???

August 14th

I was struggling with passing information in the CRUD based setup of Rails yesterday but think that the solution may be now for the attribute of the parent that I was looking to change to sit on the model of the child. This was not my creation to be fair and was the means by which the model was inherited.

August 22nd

Well this struggle actually relates to something which I encountered a couple of days ago before my holidays down to Christchurch. this was with running database migrations that were actually not required afterwards. it seems to be important to rollback a migration file before deleting it to keep the status of migrations up to date. that’s pretty much it, pretty simple but wasn’t really obvious at the time until it affected me.

September 6th

Need to recompile using webpack

Node version had changed somehow

think it changes back to default everytime that I open up a new instance of vscode

then when it is running an application on the wrong version of node it was causing issues

October like 3rd or something

Really getting lost trying to do joins in rails active record query interface and so need to look into these more. But was also very lost looking at what the pretzel operator was but figured that out after reading a few articles which cleared up that it converted it to a proc which was passed as a block to like an enumerable method. There was some benefit to this though as I feel it has cemented for me what a block is and that fact that it is only invoked by a yield and has to be passed to another method. So maybe it was worth all of this faff and feeling like I couldn’t do anything myself. Have started the Linux foundation Kubernetes course as well which I’ve found to be good so far and have a good bit better understanding of it as a result. Just need to keep going and finish it off. I have also been watching the Kubernetes documentary by honeypot for this and it was really interesting and very much highlighted that none of this would have happened without docker just blowing up so really need to look into the inner workings of docker and such. They use the analogy of Kubernetes being like the postal service and docker being like the parcels, taking care of the internals of the content, and the postal service makes sure your parcel gets to the correct place. Doesn’t matter if there is traffic or issues with air traffic they will figure it all out. I think the stamp was the cost of using Kubernetes services.

- .includes for active record loads the queries in a more efficient manner in certain instances and can prevent excess calls to the database

October 5th

Didn’t actually realise that you can’t add a where clause directly on like an association on a model

You need to like join the associated model and run the where clause on that

October 6th

Really not feeling it at the moment but that’s probably just the phase of learning I am at at the moment. Feeling like I can’t implement much and that any suggestions or actions I take are like wrong. Probably down to the new experience dynamics on the team here which means that I have probably taken on more responsibility and have a little less support and so that is a little bit of a challenge but it is all probably part of moving up that master levels thingy that Sean had. Then on top of that feel like there are some things which are obstacles in my like workflow which are impacting that smoothness and that maybe removing them would be good and make these plateaus more palatable. Things that I would like to do on this front are: setting up 2fa to be really smooth process so that I don’t have to like use my phone or even 1 password (potentially ansible is like a solution to this) part of this would be understanding how key storage and like 2fa with the likes of Github are working. it’s always been something which I never really got to grips with. Then there is the IDE which VS Code has been really slow so moving to kickstart would be good

Actions to take:

- [ ]  IDE:
    - [ ]  Set up keymappings to run neotree within neovim set up on kickstart
    - [ ]  may need to set up tmux in order to have another terminal open to set up the like windows or whatever so that I can like run git commands and all that jazz at the same time
    - [ ]  also to view like containers that I have running and like the webpack server would be good
    - [ ]  having like the Ruby LSP from shopify set up to help with like prompts for various methods and all that jazz would be good also
- [ ]  General workflow:
    - [ ]  Look into like a Yubikey
    - [ ]  Potentially ansible is like a solution for this as well?

October 19th

Okay so these are somewhat struggles but not really those ones that have wrecked my head all that much. The first is that you don’t actually have to permit all keys that are being used on the 

commit key in params has

form_with and all that jazz

- it was something along the lines of form tag used to just be like a free for all. form_for was only attributes in relation to a model and now for with is the best of both worlds or something along those lines.

git interactive rebase

- reapplying commits that have already been pushed
- interactive you can manipulate the manner in which these are reapplied

performed? helper to see if something was already rendered

then just to note that the render call happens after the full method execution

October 24th

Not actually struggling all that bad and actually proud of myself for figuring out as much as I have in relation to Google Analytics for my latest story. There was a decent bit of time required to get up to speed with the google analytics platform itself which I’m not that much of a fan of the user experience. Within this once you add the tag to your website you get some decent automatic tracking. I was struggling when trying to capture query parameters which had special characters in the url. This itself led me down the path of what are best practices for query parameters in relation to SEO. Learning to take away from this is probably that I need to learn a little more about this last sentence mentioned there. But overall it has been nice to be able to teach myself, test and implement google analytics in the supergold project mostly by myself.

October 27th

Was having an issue with adding event listeners to html elements using jquery. The listener was not working as the javascript file was being executed on load apparently. So I had to like wrap it in an anonymous function for it not to be executed immediately. Need to look into the workings of this and why this was the case as I don’t really understand it all that well tbh.

Also had a catch up with Gus about mobile apps and learned some interesting stuff. So XCode uses swift and for android the equivalent would be Kotlin. With these you can interact with the native hardware on the relevant phones. Cross platform solutions are typically just wrappers on an instance of a browser using javascript. However flutter has its own like rendering tool which can then like compete with native apps as it controls how all of the like pixels and all are rendered. 

October 30th

Other small things which I learned were some bits in relation to SEO. Just stuff like having page title is important and also like having a site map or whatever you want to call it so that browser like scripts/bots or whatever can crawl your page accurately to improve rankings and all that jazz.

October 31st

So was working with deleting a lot of data and the effects of that were somewhat interesting. saw how the cascading can be quite slow and therefore probably needs to be running in a background job. The issue is that the user doesn’t have much, if any visibility on what is happening within the process. within this I was exposed to destroy_async method for dependencies in the sql table which was introduced in rails 6. Then also with the ActiveJob object which allows you to get jobs running in the background. Additionally this 

November 2nd 

Getting failing ABC complexity in our code climate diff which is related to the following https://wiki.c2.com/?AbcMetric. Think it would be good to look into this and it is good to keep fat model and skinny controller.

November 3rd

Learned a decent bit about docker and elastic search as we were updating the version of opensearch we were using. Dockerfile is the instructions for a docker image and docker compose is like the networking of multiple containers. Elastic search is like a number of indices which is the equivalent of a database in RDBMS then there are some other equivalents but index in elastic is not the same as index in the RDBMS world.

November 6th

Found that I was having to work with github workflows and pods on kubernetes today which was good and learning a bit more about more of those fields but these weren’t without their difficulties. Then also there were some issues with a github action which we were using within our workflow which was running certain versions of chrome vs using a different version of chrome driver. Also was having to work between local, staging and prod to figure out how the move to opensearch from elastic will work.

November 8th

Need to figure out what a Content Security policy is and the implications and why of it all?

It was part of the reason a piece of a gem wasn’t working for me as it wasn’t allowing inline scripting on SuperGold. Also I was trying to squash and rebase but it like did something weird and I’d like to recover the state of my local branch before this rebase was enacted.

November 21st

Not so much a struggle but just as a means of like persisting some javascript knowledge had to try and use cookies. As part of this was just looking up what the difference is between local storage and cookies. Didn’t look into it too much but would be good to know the difference and look into it a little bit more down the line.

November 22nd

Was struggling working with the params hash in rails as it isn’t a basic hash that is returned but a special ActionController Object with associated methods. so needed to try and do some more tweaking to be able to like get the size of hash for doing some logic checks and all that jazz. Also was having to like populate a date input field via javascript and using vanilla javascript was proving to be a bit of a pain so had to look into moment.js (which I haven’t really done all that much just yet but we’ll get there). Could also do with looking into how the contents of a form submission in rails are appended as query params. 

Also think I’m a little but more up to speed with things now in the npm world but seems like we use yarn to like install javascript packages but at the same time like use npm and it all like sits on top of that. do you need node in order to be able to use npm? I don’t think you actually do but then we do use node for some things but not really sure what?

November 23rd

Ok so there were a couple of things today I think but one main one is standing out. the issue was that I was using a rails form helper to render a select with a blank option. However this was not displaying as a selectable option in the dropdown even though the native implementation from rails should have been doing so. After asking Andy, who suggested viewing the response from the server which can be done by viewing page source, I figured that it was something that was being layered on top by the client side and in this case it was selectize doing some stuff.

November 24th

Was chugging along today and made some decent progress I would say, have been using form helpers quite a bit on this story that I’m working on at the moment and have been finding them pretty easy to understand which is great. Was having a little struggle getting some form elements to reflect the state of the query params but got there after looking at the docs on options_from_collection_for_select helper docs which was a pretty satisfying way to end the week!

Need to look into how to see the changes introduced by a particular file in a particular commit in git

November 27th

Eslint is giving out about not having a package imported 

December 4th

- could do with doing a little bit on why instance variables are required and the access levels of them. For example it seems like you can change instance variables within a private method
- To summarize, the distinction between local variables and instance variables in terms of accessibility is designed to support encapsulation and to control the visibility of the internal state of objects in Ruby.
- need to look at local variables vs instance variables
    - this could be key for rails and views really

Dec 7th

margin auto and min height of viewport as 100, need to add margin auto to the footer

and also set the flex direction of the body

Dec 19th

why was it that adobe flash died, what is canvas, which was introduced in HTML5?

Jan 8th

First day back in the office and so just looking to get a handle on what are some of the elements that I am struggling the most with right now. I think my knowledge of networking still needs a lot of work really but this should hopefully be helped with a better understanding of kubernetes and docker now at this stage. Key to all of this would probably be getting a better understanding of containerisation (docker I suppose) and then following that up with like a piece on container orchestration (kubernetes). Although before doing this I think it could be good to go back over all of the computer architecture and operating system pieces to understand where all of that is ultimately coming from. Docker and Kubernetes would be integrally linked with deployment and therefore it could be good to have a description of development in git before this although actually nah, can get back to that after we have the hardware and the operating systems, jump on top of this with what a virtual machine is and the like bare metal solutions and all that jazz, then like what a hypervisor is. but all of this work begins by reading and research time dedicated to a couple of those topics and then getting that down on paper somehow. I think I should do this by writing these as private medium posts for now and getting them up to speed. these will all be interwoven in a web of different articles overtime. for now keep it simple. get an article to an acceptable standard done on Operating Systems & Computer Architecture. It may be easiest to do this for more than one hour a week to get properly into it. although the consistency of that would be beautiful. but as I think about it now it may be that two hours is required really. first task do out a rough table of contents of my manifesto. then start on the first article that makes up that series.

Jan 9th

- was not using the correct namespace to try and interact with ingress on the cluster
    - added in a plugin for the zsh cli to prevent this in the future
        - tbf I didn’t even know this was a thing
- rails routing starting using namespacing, scopes and constraints on the routes which I need to look into in greater details
    - as part of this I would also ideally need to look into when you need to like require or permit params and how all of this works
- ]

Jan 12th

- all of the things were learned about caching today
- great description here from Xavier Noria about the issues of storing an object in a cache
    - https://github.com/rails/rails/issues/43767
- main point is that instances do not survive a reload of the application
- application reload can be triggered if there is not caching of the classes as can be the case in development
- fundamentally it does not work as instances are snapshots which when serialized will not be reflective of any changes to the base class. These will be stale older versions built on an older template of the class
- there is a parallel in OOP between the class/object instance and the image/container in docker

Jan 24th

- looking at Vue the smallest bit for the first time in a whilte
- confused as to what build tools like vite/webpack do to be honest

Jan 25th

- was chatting to Gus this morning and went through some of the basics on compiling of front end assets and how its managed by like webpack or vite or whatever
- main concepts would be like building the dependency graph, tree shaking, and then like the dev server setup for hot module reloading when editing files and all of that jazz
- Gus also mentioned that like the public folder is significant most likely as it is configured on the web server to provide access to this folder from external traffic
- then we very briefly discussed tls and ssl certs for communication with external traffic which I will maybe need to look into tomorrow when I look to set up mem cache for production.

Jan 26th 

- Ok so had a remote day today which was pretty hard to make much progress with the story that I was working on to iplement memcache for check.
- To begin with I had to look into TLS which is the new name for SSL which is all a little confusing I suppose. But a server is issued an SSL certificate from a certificate authority
- this states the cipher or encryption method that is going to be used in addition to the public key from the server in question
- the client encrypts a session key using asymmetric encryption and sends it over the network to the server which has a private key with which it can they decrypt and use the session key to use symmetric encryption.
- this is everything that is behind the move from http to https with everything encrypted in transit
    - need to look into how the public key and private key relationship works
- watched a really good video on it on computerphile which showed how for authentication you can also encrypt with the private key and anyone can see that the message is from you. this would normally be done in conjuction with encrypti\ng additionally using the public key of the receiver also.
- then on top of this sockets and ports kind of came up
- the issue I was working on seems to have established a tcp socket and then was wondering how this is related to a port
- well they kind of aren’t all that related at all
- a port is kind of like a PO box where certain processes can be running
- only messages of certain formats will make sense on that port
- not sure how this is enforced or ensured to be honest so that is probably a question for Gus
- but essentially yes a domain gets you to the building but if you want to talk to the right person then you need like their room within the dorm
- e.g. if a university block you need it to go to the student that can speak the language of the message, this could potentially be a good analogy
- not entirely sure of the role of the certificate authority but essentially they seem to just be some trusted bodies for issuing the certificates that are hosted on servers

01 Feb

- was working a little on a shared branch for the last couple of days which has highlighted some things with git
- rebasing and trying to use git reset would be an issue in this regard
- git reset only affects your local branch so would then have to destructively git push —force on this which is dangerous at the best of times but especially if you are on a shared branch
- need to look into —force-with-lease to for rebasing in these cases in the future
- anything you do in git is only local until you push of course which is something that is only kind of hitting home now
- git revert is a better option, especially when working on a shared branch

02 Feb

- had a very good morning of conversations about include and extend. So, all classes/modules are autoloaded by rails if they live within the app folder I am almost certain
    - this would actually probably be a good point to inspect how Xavier Noria’s zeitwerk works to see how this autoloading is taken care of
    - if the code is living in the lib folder then it will have to be explicity required
- then yesterday I had to have a little clarification on self and class methods. So essentially within a class self is just a contextual reference. For example self.method_name will be referencing the class but self.atrribute_name (not even sure you can do this in ruby) if it is within an instance method will be referencing the instance of the class.
- Then finally include includes all of the instance (in,in,in) whereas extend makes them available as class methods on the class
- You need to extend the module with `ActiveSupport::Concern` in order for the `ActiveSupport::Concern#included` and `#class_methods` methods to work properly.
- 
- When we extend the module with `ActiveSupport::Concern` we are putting it on the ancestors chain of `ABC`, thus the methods of `ActiveSupport::Concern` are available as module methods of `ABC`. This does not happen when you use `include` and the `included` method called is actual
- Modules cannot be instantiated.
- The **super** keyword is used to call a method of the same name in the superclass.
- but then again modules can also just be used for like namespacing of directories in rails application
- lots was learned on this front today
- ancestors method gives the ancestry of a particular class
- then there is just prepend which is something a little different that I need to look into

07 Feb

Ok so I made like pretty decent progress towards using vim as my IDE there the other day. I now know how to setup nvim using kickstart pretty easily and it all just lives in .config/nvim which is nice. I’ve made a fork of the repo and can push any changes towards that. I have made note of a couple of things that are preventing me from using it as the main IDE which I need to resolve:

1. I can’t search across the git repo for a particular word
2. I can’t use any of my shell commands at present and my aliases such as ccl
    1. to be fair maybe I shouldn’t be running them within the IDE and maybe it should be in another window
3. window managing is still a little bit of a struggle to be honest

09 Feb

Ok so it’s like 5 to 5 but just have a couple of things that I have to jot down. First of these is that I finally remapped my cmd keys on my keyboard cause I really need access to the modifier keys as I look to move towards using nvim way more. Second thing then is the significance of the template tag in html for conditional rendering of objects which is really good and had a little look at the DOM in greater details as a result. need to look into this in more detail tbh to understand if it has implications for the virtual dom and that behaviour. oh yeah and then the third thing was just using the built in /remind functionality in slack to give myself reminders to do different things.

15 Feb

Had the first few days of PCO which were a little tricky with my level of experience I found. Just not having a truly deep understanding of systems really was the main struggle. E.g how the APIs work and how we would interact with them, using terraform for aws and just getting logging, domains and all of that jazz set up. It was really good yesterday to start using terraform to plug in to aws though. Just had to get the access keys going and then it was good to go really.

Next is having any sort of notion about how Supplejack works and also the docker and kubernetes setup. will be good to know how docker builds the image and all of that jazz.

16 Feb

Had a look at standardising linting using the standard gem which seemed promising even though it is a little opinionated. The main breaking change was around argument forwarding when it was being forwarded anonymously but then had a conditional to check for the presence of a block in the forwarded argument so need to check that out.

In looking into this in a little more detail it became clear that *args just popped something into an array and **kwargs just pops something into a dictionary.

22 Feb

There has been so much to try and take in these last few days as we’ve started out on the PCO project. We’ve been using flux to monitor changes on our kubernetes repo containing all the yamls of the kubernetes resources so I now kind of know what’s going on there. On the rails side of things the rails db:create and all of those commands are only related to active record setup with migrations and all of that jazz. 

There was lots of encrypting of secrets which I didn’t really understand all that well. Had to brew install kubeseal which I don’t really know anything about but it takes like a secret encoded in base64, again another thing that I need to understand how that is working, and creates a sealed secret on kubernetes. Because like regular secrets aren’t all that secure.

Also was mentioned that rails has a secret functionality which generates some sort of secret which is like used for signing cookies in the application or whatever.

Also would be good to understand how some stuff like the master key is encrypting the credentials file in rails.

The Base64 padding character is the Equal sign (=) and is placed at the end of encoded data.

So base64 is like the indices associated with 64 characters after converting the binary of something

logs of rails app by default go to specified folder but good to send them to standard out so that you can access them from 

March 6th

For where I’m at in my learning journey really not enough entries going in here but to be fair a lot of the recent stuff has been a bit more project specific. One thing which I have been looking into a little is ssh keys given that they are used everywhere and I have a little better understanding of them now but could do with going over how they are used and the different use cases between like communication and access eg. cloning a repo or logging into aws and then in contrast to the likes of TLS over TCP and SSL and all of that jazz. Then I checkout out about meta programming in ruby and had a good chat with Gus about that stuff so have a decent bit better understanding about the startup of MRI how the base classes are implemented in C and then also just the Class and the fact that everything is an object in ruby. Then finally just like some use cases for heavy meta programming such as active record I believe and must just keep reading that book then

March 8th

The native structures of yaml and the ability to have like arrays in yaml or whatever. Then also how to invoke the right libraries and environments within both rspec and in rake tasks. All kind of links to the issue of all things being like auto loaded across files in a rails application so could do with looking into how zeitwerk works.

March 12th

So yesterday I probably should have added in an entry around my lack of understanding of some of the components within our infrastructure. The main pieces that I didn’t have enough knowledge on and that I need to look into more in the future are NAT, Internet Gateway, the functioning of the CDN and where it relates to the DNS. It would have to be after resolving the DNS and querying that it hits the CDN first before getting to either the load balancer or definitely before we get the actual application. Then today I was setting up the frontend of one of the applications for the PCO work, i.e the NZL front end which will be querying the pco api. So to do this was interacting a little with the initialisation of a rails application and just how you can decompose aspects of the rails application within the config/application.rb file which is cool. This interacted with railties which are something I don’t know all that much about but seem to be a number of libraries that are available within rails to provide different functionality.

March 13th

Was going pretty okay today to be honest. Just had to get some help from Richard for setting up secrets on kubernetes and sealing them and all of that jazz. Having the secrets living on the kubernetes cluster is just easier for managing secrets than having to have these living within each pod. For some reason if the likes of the credentials file lives on the pod then it would need to be rebuild more often. that I don’t really know. Need to look into what the secret_key_base is that is within rails for like encrypting session/cookie data or something. Sessions relate to the server and cookies to the browser I believe?

Another thing which I would like to look into is the params hash and see how exactly rails pulls out params from the request body? I know how it would take any query parameters in the url and then any fields from form submission too.

Actually have one other thing which is why exactly sealed secrets aren’t just the native way of doing things for secrets and also why it is that you have to base64 encode them?

March 19th

Had some issues with using factory bot where it couldn’t set fields on meta data fields which would be no issue when using active record because of the way it operates but mongoid does it slightly differently so need to look into how all of this operates. so it would be good to look into how this is working under the hood

March 21st

Ok so today had some minor struggles with bootstrap but think it is clear enough that there is a javascript package which implements the functionality to create the relevant components and interact with the styling and component creation in javascript. So yeah basically can just probably yarn/npm install and then import those files within the javascript to have access to them?

Also just had a little struggle with the rails configuration files. seems like what happens is that the rails config/environment loads the initial rails application with the settings as described in config/application. once an instance of Rails is up and running I think it will then check if there are specific environment settings that should be set such as test/dev/uat/staging etc. Another question I have is how exactly does bundle check what the environment is at present?

march 22nd

Ok so probably related to some of the above but something that is giving me a better understanding of the frontend ecosystem is the fact that vite is actually built using node. I think up until this point I didn’t really see the significance of node and why would you need server side javascript. However with this vite is able to process lots of frontend related pieces on the backend and then build and distribute the minified assets for the production image.

March 27th

Not actually struggling with this too much to be fair but moreso jotting this down as a point of note. Had been thinking why don’t database solutions also just perform the role of search solutions since they already have the data however they are more focussed about looking after the issues relating to acid such as guaranteeing state and transactions and then like scalability and fault tolerance. Search solutions look after indexing and probably looking after like all the api integrations for a number of different languages. e.g. there is sunspot which is the client library for ruby for solr. Another thing that came to light was that I didn’t realise that Zeitwerk is set up to autoload user defined classes within the app folder by default in a rails application. But there is additionally the Bundler.require method which can autoload the gems for the different environments within the project.

April 16th

Okay so it was a big enough time for some learnings as part of the software struggles diary. Yesterday I was working on the technical documents for PCO and learned a lot from doing this. Learned how the CDN sits between the DNS and the load balancer to respond with as much cached data as possible without having to interact with the server. Then additionally was making some sass changes to the bootstrap components and wiring it all up using vite so that was pretty good.

April 18th

Had a couple of frustrating hours this morning really fiddling about with navbars and assets (specifically svgs) in vite and bootstrap. Essentially seems like the navbar has its own peculiar behaviour in bootstrap operating a little bit outside of the grid system which I just needed to come to terms with really. Then with vite in terms of svg there wasn’t an easy way to change the colour of the svgs when there are included as compiled assets in vite. there is like an inline-svg gem which gives you access to read the svg file I think (question: is the file even accessible? probably yeah) but anyway that only works with sprockets and webpack really. 

May 2nd

Was struggling with an awkward story where we have to render html files from s3 bucket. Syncing them down was actually so simple using the aws cli (which is basically just using python although not sure what protocol it would be using to communicate). Then it required some awkward kind of rails routing which highlighted that I am not au fait with that really.  the params attribute lets you override the default lookup on the resource which you are looking to identify and that the as attribute just like updates the naming conventions on the url and path helpers that are available.

May 7th 

I had a pretty slow going day yesterday productivity wise finding it hard to kick the inertia and get going.  But today is going to be a more productive day. Was struggling today with specifiying a different response type of .jpg for a static image so really need to look into the content-type/mime-type that is specified in a http request and what the significance is of specifying the format. good article from Akhsay saved on pocket on this. Also by default the public folder is at the root of the application on a web server which is another new thing I learned. Then I was also messing about trying to manually add binaries to a pod but I should have just updated the docker file of the image of the pod that was on the cluster. I definitely have learned more about the linux OS and the things that are available. need to look into the alpine distribution of Linux in a little more detail but I think it is just a very lightweight distro. Was messing around with the dockerfile for the production image and adding in the cli package which was my first time having a look at the package website for all those that are available for Alpine.

May 8th

Learned a lot about mounting of volumes from storage onto the operating system file system. Mount needs to maintain metadata file of the structure of the users filesystem. /media in linux refers to mount from a removable device whereas /mnt is like a temporary reference for th location.

may 15th

Really struggled with a story for rendering files from EFS. but it was all good really. had the issue with the /mnt understanding as outlined above. Then given that it was set up outside of the normal rails constructs my code organisation was all over the place with the controller having far too much logic. Moved that out of the controller to the model and set up some custom execptions that needed to be handled and rescued from in the controller. Also got a little better using the likes of faker and factory bot in testing. Then there was the issue with the autoloader in rails not working for one of my file structures as I wasn’t following the conventions of each module having to have a corresponding directory name which is something that I need to look into in more detail. For code organisation I think that I need to have a look at the Sandi Metz book.

May 20th

This one is to do with testing is the main application I would say. Was just looking at the ruby implementation of Selenium to get that up and running for doing some accessibility tests. The main thing was just the distinction between the client and the driver. You have to register the driver with capybara but you then have the client configuration for running these automated tests which sends the requests to the web driver which is able to in turn interact with. the relevant browser.

May 28th

Was struggling today with FactoryBot quite a bit but just got stuck into the docs which I found really beneficial and a lot more sustainable a manner for moving forward than asking straight away.

July 5th

Things have been going pretty well recently I would say. I’m still a bit slower to do things but I am probably doing slightly more advanced things. In the last few days I’ve been working on caching which has been pretty straightforward really. These are just controlled on the server (for the most part) and specify how long that response will be cached by the server/cdn max-age is how long the client will cache for and s-maxage is how long servers and shared resources will cache the result. As part of this I came across the fact that we were creating source maps in production on two of our applications.

I have also moved over to using neovim exclusively for development as opposed to VScode which is pretty cool I would say. Also I have made good strides understanding configuration in rails and middle ware. I think I may have done another blog post on something but I can’t quite remember right now. I have done a decent bit of research on networking and TCP and TLS and in fact most of the OSI stack now makes a decent amount of sense to me.

Additionally I have learned much more about the build process using vite on our current projects but still have a little while to go. (see reference to source maps above). Would be good to have a little more insight on this for sure. I have also done bits of research on Linux and have a better understanding of the command line that is available as part of this but could do with looking into this in more detail.

I have also just this morning been looking into serialisation again with this SO post being a good summary at this point. https://stackoverflow.com/questions/65478382/why-is-serialisation-necessary-for-sending-data 

Finally I have been reading POODR by Sandi metz which has been good for thinking about design in Ruby. I would also be very keen for doing Greg Molnars course on security in rails when that comes out.

Mon 8th July

Okay so I learned something a little new about ruby today. This is in relation to the rails console essentially. By default I think it will use the irb console with ruby but the pry-rails gem can configure it to use pry as opposed to irb. Could do a quick little investigation into what they are exactly.

Tues 9th July

I could do with looking into multiplexing and how it works as it seems to be a kind of important part of my job to understand it at a high level. It involves splitting up a single communication connection so that it can communicate a number of different messages across the network. Think how different frequencies of radio station are available. They are all available on a similar pich or something. Lamda is an anonymous function in mathematics.

Wed 24 July

Was watching the node documentary and this brought the concepts of computer architecture to the forefront again. I did some good research on this and understood how most things are driven from the CPU, memory and disk in the Von Neumann architecture of course. There must be some logic embedded in the CPU (think this is where ARM and all of that need to have code within it). It also intercepts with the OS of course and how it manages the interaction of programs with this hardware and getting access to the CPU.

The electrical elements and how they are generated is something that I could probably do with understanding at a high level (but lower level than I currently have). The distinction between I/O and CPU time which was discussed in node could be good to think about a little more also. I suppose once the message has been sent from CPU or is waiting for network to respond there is no reason for a thread in the CPU to be waiting but can be reassigned. This also brings up the topic of concurrency and multi threading. Could definitely do with learning about this in the ruby context. I need to understand how a CPU is subdivided so that a CPU can run many tasks in paralell. The distinction between concurrency and parallel would also be good to hash out.

Also had a little look into pry as I look to improve my debugging game and I really feel that I wasn’t using this to it’s full capacity to improve my productivity in ruby.  REPLs are tailored for interactive programming and debugging, whereas CLIs are designed for executing a wide range of commands and managing the operating system.

Also I could do with understanding detached head state in git very much so. I think it is just when the head is not pointing to a particular branch. This means that if you were to look to push this anywhere there is nowhere to push to. To resolve can just checkout a new branch, of if you want to preserve the changes you have made, push to a new branch.

Monday 5th August

Pretty happy with myself this morning even if it was a bit of a struggle. Have the docker container for the new application up and running. I understand the layers of the image a little better which is nice.

Tuesday 6th August

Had a decent bit of research to do after work yesterday so these are some of the learnings/thoughts I had as a result of this work. Sealed secrets that I have used in the past in kubernetes is actually a third party thing as Kubernetes does not encrypt secrets but only base64 encodes them. Not really sure why they bother with the base64 encoding but seems like it could just be useful for parsing the config/yaml files. Then on top of that was doing a decent bit of docker yesterday getting a new project set up and I’m a lot more comfortable with that now. There were a couple of things that came out of this. First that linux is a kernel and not an operating system which seems to be run in conjunction with GNU normally. All the distributions on top of this such as Debian and Ubuntu are built on top of this combination.

Monday August 12th

Have been setting up my first api from scratch which has all been pretty humbling for the scale of the task. But to be fair this is just my first time doing it. I have been like overloading the controller with far too much functionality which will probably need to be move to it’s own class which in a rails app with no model present will probably just have to live in the app/lib folder I suppose. There were some additional considerations with the api that I hadn’t really considered though. It needs to be set up with authentication which at present is just taken care of on nginx. SSL is also somehow configured on nginx which I don’t really know how to manage. I did learn a lot setting up the kubernetes cluster and the docker images for the application in addition to all of the CI stuff which isn’t all that bad. But with the api itself I was not really aware about best practices with OpenAPI which I think would be very good to be up to speed with and just even best practices with naming conventions on the routes and all. Beyond that I should be more up to speed with like managing API keys and authentication in general I feel.

Tuesday 13th August

Implemented first API which felt pretty decent. Used swagger to comply with OpenAPI and provide a convenient UI for testing the api.

Thursday September 9th
Ok so I was very much lost in the woods as per the analogy of expertise from the 10000 hours podcast where it was said that a measure of excellence was to be comfortable wherever you are dropped in a codebase, or in this case in the woods, and that you can make your way through.
I was very much in the state of going around in circles and not knowing where to go to find the right path.
Then even this experience was preventing me from finding my way out, addling my brain.
But then I did think of that reference in Infinite Jest about pursuing excellence where it says that many quit just when they are at the end of a plateau as they don't know just how close they are to breaking through.
This was very much me over the last little while but I will get better. 


Monday 30th September
Was struggling today with the lookaround characters in regex machine which I don't really understand all that much.
The negative symbol is a lookaround character and so it behaves differently in the regex machine
