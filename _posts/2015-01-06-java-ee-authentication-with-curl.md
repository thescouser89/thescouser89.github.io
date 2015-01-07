---
title: Java EE Authentication with Curl
layout: post
---
If you've always wondered how to authenticate to a standard Java EE
authentication form using the _curl_ command, this page is for you!

* First we'll obtain a session id from the server.

  {% highlight bash %}
  curl -v -c cookies.txt http://localhost/login/index.jsp
  {% endhighlight %}

  The session id will be stored as a cookie in the file _cookies.txt_.


* Next we'll use the session id to authenticate the user.

  {% highlight bash %}
  curl -L -v -b cookies.txt \
       -d 'j_username=<username>&j_password=<password>' \
       http://localhost/login/j_security_check
  {% endhighlight %}


* Finally once the session id is authenticated, we can use it to do secured
  operations.

  {% highlight bash %}
  curl -v -b cookies.txt http://localhost/list
  {% endhighlight %}

Hope that was useful :)
