---
layout: 2columns
title: Javascript SDK
categories: guides
tags: SDKs
---


#Javascript SDK

The JavaScript SDK enables you to access the API from a Web Browser.
It  hides all the complexity of OAuth 2.0 and lets you focus on writing application code.

Just include the following source script in your application
	
	<script src="http://static.mlstatic.com/org-img/sdk/mercadolibre-1.0.1.js"></script>

For https use: 

    <script src="https://a248.e.akamai.net/secure.mlstatic.com/org-img/sdk/mercadolibre-1.0.1.js"></script>
	
Initialize the API with your client_id as follows:

{% highlight javascript %}
MELI.init({client_id: 6586});
{% endhighlight %}
	

That's it. Afterwards, this line of code will show the First Name of your registration in MELI:

{% highlight javascript %}
MELI.get(
  "/users/me",{},
    function(data) { alert("Hello "+data[2].first_name) }
);
{% endhighlight %}

Under the hood, the JSSDK checks that:
- You are actually you
- The app “melidev” (client_id #6586 in this example) is the actual caller
- You authorized the app “melidev” to access your data
    
If you want to contribute or you find something that needs to be fixed, just fork our SDK in [GitHub](https://github.com/mercadolibre/mercadolibre.js) and pull requests as needed or get in touch
through our [contact](/discuss) page


##API Methods

<div class="ch-box">
	<div id="init">
		<p><strong>init</strong>(options)</p>
		<div>
			<p>MELI SDK javascript initilization.<br/> 
				In order to connect with Mercadolibre APIs you must add initial <strong>options</strong> in MELI initialization. 
			</p>
			<p>This method initialize OAuth protocol in MELI</p>

<code>client_id</code> ( int ) - mandatory. <br/> 
	
&nbsp;&nbsp;&nbsp;&nbsp;Application <strong>ID</strong> to retrieve the corresponding access tokens created with the <a href="http://applications.mercadolibre.com/">application manager</a> <br/> 

<code>xauth_domain</code> ( String ) - optional. <br/> 
	
&nbsp;&nbsp;&nbsp;&nbsp;<br/> 

<code>xd_url</code> ( String ) - optional. <br/> 
	
&nbsp;&nbsp;&nbsp;&nbsp;<br/> 

<code>xauth_protocol</code> ( String ) - optional. <br/> 
	
&nbsp;&nbsp;&nbsp;&nbsp;<br/> 


{% highlight javascript %}
/**
 * Use your application ID to retrieve the corresponding access tokens 
 * created with the application manager
 */
MELI.init({ client_id: 6586 });
{% endhighlight %}

<h2>HTTPS connection</h2>

<p>If you site runs over <strong>HTTPS</strong> protocol you must define these other options:</p>


{% highlight javascript %}
/**
 * To connect using https protocol you need to complete xd_url parameter.
 *     xauth_protocol + xauth_domain + xauth_port (opcional) + xd_url
 *
 * Example: 
 * xauth_protocol: "https://"
 * xauth_domain: "secure.mlstatic.com"
 * xauth_port: default to empty (80)
 * xd_url: /org-img/sdk/xd-1.0.1.html
 * xd_url sera:
 * 
 * Connecting to https://secure.mlstatic.com/org-img/sdk/xd-1.0.1.html
 */ 
MELI.init({client_id: 6586,
    xauth_protocol: "https://",
	xauth_domain: "secure.mlstatic.com",
	xd_url: "/org-img/sdk/xd-1.0.1.html"
});
{% endhighlight %}
		</div>
	</div>
</div>
<script>
	var foo = $("#init").expando();
</script>

<div class="ch-box">
	<div id="login">
		<p><strong>login</strong>(callback)</p>
		<div>
			<p>Login in mercadolibre. </p>
			<p>This method will open window popup to complete login process in mercadolibre .</p>  

<code>callback</code> ( function )<br/> 
	
&nbsp;&nbsp;&nbsp;&nbsp;<p>In order to login in Mercadolibre.com you can use this method passing a callback function parameter. This function is called when user login process is completed.</p>

{% highlight javascript %}
/**
 * Login into mercadolibre
 */
MELI.login(function() {
	// Your code here
});
{% endhighlight %}
		</div>
	</div>
</div>
<script>
	var foo = $("#login").expando();
</script>

<div class="ch-box">
	<div id="logout">
		<p><strong>logout</strong>()</p>
		<div>
			<p>Logout from mercadolibre. This method completes logout process expiring access tokens and login out from mercadolibre.com site</p>
{% highlight javascript %}
/**
 * Logouts MELI from mercadolibre and invalidates access token.
 */
MELI.logout();
{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#logout").expando();
</script>

<div class="ch-box">
	<div id="getToken">
		<p><strong><strong>getToken</strong>()</strong></p>
		<div>
			<p>Obtains the token, if the user is logged.</p>

<p>Following autorization state of the user it retrieves necessary token to connect with mercadolibre APIs.</p>
{% highlight javascript %}
if(!MELI.getToken()) {
	// Your code here
} 

{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#getToken").expando();
</script>


<div class="ch-box">
	<div id="getLoginStatus">
		<p><strong>getLoginStatus</strong>(callback)</p>
		<div>
			<p>Retrieves logins status</p>
			<p>They are three possible status:</p>

<code>callback</code> ( function )<br/> 
	
&nbsp;&nbsp;&nbsp;&nbsp;<p></p>

			<ol class="ch-list">
				<li><code>UNKNOWN</code></li>
				<li><code>NOT_AUTHORIZED</code></li>
				<li><code>AUTHORIZED</code></li>
			</ol>
			
{% highlight javascript %}
/**
 * Retrieves the autorization state
 */
MELI.getLoginStatus(function(data) {
	// Your code here
});
{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#getLoginStatus").expando();
</script>

<div class="ch-box">
	<div id="get">
		<p><strong>get</strong>(url, params, callback)</p>
		<div>
			<p>Executes a GET request retrieving information identified by the resource.</p>
			<p></p>	
			
{% highlight javascript %}
/**
 * Invokes https://api.mercadolibre.com/users/me?access_token=...
 *
 */
MELI.get('/users/me', null, function(data) {
    // Your code here
    // var name = data[2]
});
{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#get").expando();
</script>



<div class="ch-box">
	<div id="post">
		<p><strong>post</strong>(url, params, callback)</p>
		<div>
			<p>Executes a POST request creating a new resource using javascript SDK. </p>
{% highlight javascript %}
MELI.post(url, params, function(data) {
	// Your code here
});
{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#post").expando();
</script>



<div class="ch-box">
	<div id="put">
		<p><strong>put</strong>(url, params, callback)</p>
		<div>
			<p>Executes a PUT request changing a resource using javascript SDK. </p>

{% highlight javascript %}
MELI.put(url, params, function(data) {
	// Your code here
});{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#put").expando();
</script>



<div class="ch-box">
	<div id="remove">
		<p><strong>remove</strong>((url, params, callback))</p>
		<div>
			<p>Executes a DELETE request deleting a resource using javascript SDK. </p>
{% highlight javascript %}
MELI.remove(url, params, function(data) {
	// Your code here
});
{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#remove").expando();
</script>
