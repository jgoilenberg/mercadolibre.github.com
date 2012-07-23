---
layout: 2columns
title: Javascript SDK API
categories: guides
tags: SDKs
---


#Javascript SDK API

<div id="init">
	<ul>
		<li><a href="#init-tab1">init API</a></li>
		<li><a href="#init-tab2">Example</a></li>
	</ul>
	<div>
		<div id="init-tab1">
			<p><strong>init</strong>(options)</p>
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

		</div>
		<div id="init-tab2">
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
	var foo = $("#init").tabNavigator();
</script>





<div id="login">
	<ul>
		<li><a href="#login-tab1">login API</a></li>
		<li><a href="#login-tab2">Example</a></li>
	</ul>
	<div>
		<div id="login-tab1">
			<p>Login in mercadolibre. </p>
			<p>This method will open window popup to complete login process in mercadolibre .</p>  

<code>callback</code> ( function )<br/> 
	
&nbsp;&nbsp;&nbsp;&nbsp;<p>In order to login in Mercadolibre.com you can use this method passing a callback function parameter. This function is called when user login process is completed.</p>
		<p><strong>login</strong>(callback)</p>

		</div>
		<div id="login-tab2">
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
	var foo = $("#login").tabNavigator();
</script>

<div id="logout">
	<ul>
		<li><a href="#logout-tab1">logout API</a></li>
		<li><a href="#logout-tab2">Example</a></li>
	</ul>
	<div>
		<div id="logout-tab1">
			<p>Logout from mercadolibre. This method completes logout process expiring access tokens and login out from mercadolibre.com site</p>
		<p><strong>logout</strong>()</p>
		</div>
		<div id="logout-tab2">
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
	var foo = $("#logout").tabNavigator();
</script>



<div id="getToken">
	<ul>
		<li><a href="#getToken-tab1">getToken API</a></li>
		<li><a href="#getToken-tab2">Example</a></li>
	</ul>
	<div>
		<div id="get-tab1">
		<p>Following autorization state of the user it retrieves necessary token to connect with mercadolibre APIs.</p>
		<p>Obtains the token, if the user is logged.</p>
		<p><strong><strong>getToken</strong>()</strong></p>
		</div>
		<div id="getToken-tab2">
{% highlight javascript %}
if(!MELI.getToken()) {
	// Your code here
} 

{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#getToken").tabNavigator();
</script>



<div id="getLoginStatus">
	<ul>
		<li><a href="#getLoginStatus-tab1">getLoginStatus API</a></li>
		<li><a href="#getLoginStatus-tab2">Example</a></li>
	</ul>
	<div>
		<div id="getLoginStatus-tab1">
		<p><strong>getLoginStatus</strong>(callback)</p>
			<p>Retrieves logins status</p>
			<p>They are three possible status:</p>

			<code>callback</code> ( function )<br/> 
			&nbsp;&nbsp;&nbsp;&nbsp;<p></p>

			<ol class="ch-list">
				<li><code>UNKNOWN</code></li>
				<li><code>NOT_AUTHORIZED</code></li>
				<li><code>AUTHORIZED</code></li>
			</ol>

		</div>
		<div id="getLoginStatus-tab2">
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
	var foo = $("#getLoginStatus").tabNavigator();
</script>


<div id="get">
	<ul>
		<li><a href="#get-tab1">get API</a></li>
		<li><a href="#get-tab2">Example</a></li>
	</ul>
	<div>
		<div id="get-tab1">
			<p>Executes a GET request retrieving information identified by the resource.</p>
		<p><strong>get</strong>(url, params, callback)</p>
		</div>
		<div id="get-tab2">
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
	var foo = $("#get").tabNavigator();
</script>



<div id="post">
	<ul>
		<li><a href="#post-tab1">post API</a></li>
		<li><a href="#post-tab2">Example</a></li>
	</ul>
	<div>
		<div id="post-tab1">
			<p>Executes a POST request creating a new resource using javascript SDK. </p>
		<p><strong>post</strong>(url, params, callback)</p>
		</div>
		<div id="post-tab2">
{% highlight javascript %}
MELI.post(url, params, function(data) {
	// Your code here
});
{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#post").tabNavigator();
</script>




<div id="put">
	<ul>
		<li><a href="#put-tab1">put API</a></li>
		<li><a href="#put-tab2">Example</a></li>
	</ul>
	<div>
		<div id="put-tab1">
			<p>Executes a PUT request changing a resource using javascript SDK. </p>
		<p><strong>put</strong>(url, params, callback)</p>
		</div>
		<div id="put-tab2">
{% highlight javascript %}
MELI.put(url, params, function(data) {
	// Your code here
});{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#put").tabNavigator();
</script>



<div id="remove">
	<ul>
		<li><a href="#remove-tab1">remove API</a></li>
		<li><a href="#remove-tab2">Example</a></li>
	</ul>
	<div>
		<div id="remove-tab1">
			<p>Executes a DELETE request deleting a resource using javascript SDK. </p>
			<p><strong>remove</strong>((url, params, callback))</p>
		</div>
		<div id="remove-tab2">
{% highlight javascript %}
MELI.remove(url, params, function(data) {
	// Your code here
});
{% endhighlight %}
		</div>
	</div>
</div>

<script>
	var foo = $("#remove").tabNavigator();
</script>

