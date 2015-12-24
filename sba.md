***Session Based Authentication***

##what is session based Authentication?##
     
       ->In Session-based Authentication the Server does all the heavy lifting server-side. Broadly speaking a client authenticates with its credentials and receives a session_id (which can be stored in a cookie) and attaches this to every subsequent outgoing request. So this could be considered a "token" as it is the equivalent of a set of credentials.

       ->It is stateful. It associates the identifier with a user account (e.g. in memory or in a database). It can restrict or limit this session to certain operations or a certain time period and can invalidate it if there are security concern and more importantly it can do and change all of this on the fly. Furthermore it can log the users every move on the website.
       ->The session management is server responsibilty. When the session is created, a session token is generated and sent to the client (and stored in a cookie). After that, in the next requests betwen client and server, the client sends the token (usually) as an HTTP cookie. All session data is stored on the server, the client only stores the token.
       
       ->A session is defined as the time during which a Web client is actively logged onto a server with a cookie. To specify settings that enable and control session authentication, you edit the Web Site document or the Server document, depending on your configuration.

       ->To use session-based authentication, Web clients must use a browser that supports cookies. 

       ->Session-based authentication differs in that the user's name and password information is sent over the network only the first time the user logs in to a server, not each time a request is posted. After login, the user's name and logon information is stored in a cookie in the user's browser, and the browser sends the cookie to the server with each request. Before honoring a request, the server verifies the information in the cookie and uses the cookie contents to identify the logged-in user.

       ->The session is only valid within the browser in which the login was performed. If the user shuts down the browser in which the session login took place, the user's session will be ended and the cookie will be destroyed.

       
##Benefits##
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
        => session-based authentication provides greater control over user interaction than basic  authentication.

	=> server-side session management takes advantage of client-side cookie management.

	=> server-side session management takes advantage of client-side cookie management.

	=> you can create a session only for an authenticated user if you want.

	=> The information is encrypted in most cases.

	=> Storing session client-side is quite convenient in distributed environment, because it eliminates need for designing solution for central session management on server side.

	=> Sessions are maintained on the server by a session identifier which can be passed back and forward between the client and server when transmitting and receiving requests.

##Solution##

       
        * Authentication only works with some secret key. And of course this key should be kept secret. 

	   -> Never store a password in plaintext in your database. There are several libraries available to make it secure.

	   -> bcrypt: It's been optimized to hash passwords. It automatically generates a salt and hashes the password multiple times (rounds). In addition the generated hash-string contains everything needed: Number of rounds, salt and hash. Though you just need to store this one String and there's no need to write anything by hand.

	   -> rounds: This is simply how often the password should be hashed. When using 5000 rounds the hashing function will return the hash of the hash of the hash of the hash of the password. There's basically a single reason to do this: It costs CPU Power! This means: When someone tries to bruteforce your hash, it takes 5000 times longer when using 5000 rounds. For your application itself it doesn't matter that much: If the user knows his password, he will not recognize, if the server took 0.0004ms or 2ms to validate it.

	   -> Keep authentication and basic account data isolated.

	   -> Allow users to stay logged in while browsing different apps.

##Implementation##

           The are several methods used in an implementation.

	   *** Public methods ***

	   -> synchronized static PasswordAuthentication -requestPasswordAuthentication(String rHost, InetAddress rAddr, int rPort, String rProtocol, String rPrompt, String rScheme)
	   Invokes the methods of the registered authenticator to get the authentication information.

	   -> static PasswordAuthentication -requestPasswordAuthentication(String rHost, InetAddress rAddr, int rPort, String rProtocol, String rPrompt, String rScheme, URL rURL, Authenticator.RequestorType reqType)
	   Invokes the methods of the registered authenticator to get the authentication information.

	   -> static void - setDefault(Authenticator)set as the default authenticator.

	   *** Protected methods ***

	   -> final String	- getRequestingHost() returns the host name of the connection that request authentication.

	   -> final int - getRequestingPort()
	   Returns the port of the connection that requests authorization.
	  
	  -> final InetAddress - getRequestingSite()
	  Returns the address of the connection that requests authorization or null if unknown.




          
