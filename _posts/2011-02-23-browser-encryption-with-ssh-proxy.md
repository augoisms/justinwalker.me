---
layout: post
title: Browser Encryption with SSH Proxy
date: '2011-02-23 11:58:39'
tags:
- encryption
- proxy
- security
- ssh
- terminal
---

<img class="alignnone size-full wp-image-119" title="firefox proxy settings" src="http://justinwalker.me/wp-content/uploads/2011/02/firefox-proxy-settings.png" alt="screen shot of firefox proxy settings" width="726" height="694" />
<div>
<div>
<div><code>ssh -ND 9999 username@yourdomain.com</code></div>
<div style="padding-top:20px;">

I’ve been actively using  VPN for several months now whenever I am not at home and using a public wifi network.  These days with so much of our lives on the web, you can never be too careful.  One thing I found was that, depending on the situation, VPN was not always a great solution.  Work, school, coffee shops, or other providers of wifi may block known VPN services, especially if they have some kind content blocking system in place.  So how do you protect data when your VPN is not an options? The answer is SSH Proxy.  I saw this article on Lifehacker several weeks ago, and it has proven to be a great tool.  With just a one line command at the terminal prompt you can establish an SSH tunnel from your computer to the hosting server of your own website.  From there you can configure your browser to connect to the port that you opened.  Check out the link for instructions on how to do this.  I also found that this was a great option when using a public computer, where installing VPN software may not be an option or too much of a hassle.  Does anyone use a different method of encrypting their browsing session other than VPN or SSH proxy?

</div>
<div>

Source: <a href="http://lifehacker.com/#!237227/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy">Lifehacker</a>

</div>
</div>
</div>