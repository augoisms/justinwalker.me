---
layout: post
title: Access IIS Localhost From Another Computer
date: '2014-07-07 21:26:25'
tags:
- visual-studio
- windows
- iis
- web-development
---

**UPDATE 2019-01-26**

The steps below probably still work, but since then I've been using [ngrok](https://ngrok.com/). Much easier!

---

I regularly need to test a website I'm working on in another browser or on another device, like an iPad or an iPhone. When running an apache server in OS X you can you simply point your mobile device to your Mac's IP address. If you're developing in Visual Studio and using IIS you will need to configure a few things to get it working. The following steps got the job done. Big thanks to my coworker, [Aaron](http://www.aaronholmes.net/), who helped put this together.

1. Open ```cmd``` as an administrator.

2. Allow the ports to be accessed by the firewall.

		
		> netsh advfirewall firewall add rule name="Open Port 3000" dir=in action=allow protocol=TCP localport=3000
		
	Here we are assuming that my project is on port 3000.

3. Allow IIS to use your IP and machine hostnames. You can choose to use both or just one. 

		> netsh http add urlacl url=http://pc-hostname:3000/ user=everyone
		> netsh http add urlacl url=http://10.0.1.10:3000/ user=everyone

	Here we are assuming the IP address of my machine is 10.0.1.10

4. Add the hostnames to your local IIS configuration.

	A) Navigate to *"Documents\IISExpress\config"*<br>
    B) Open "applicationhost.config"<br>
    C) Locate the applications you need to enable remote access for. In the case of my "RemoteAccess" project, you're looking for this:<br>

```xml
<site name="RemoteAccess.web" id="17">
  <application path="/" applicationPool="Clr4IntegratedAppPool">
     <virtualDirectory path="/" physicalPath="C:\Users\Justin Walker\Documents\Visual Studio 2013\Projects\Remote Access\RemoteAccess.Web" />
  </application>
  <bindings>
     <binding protocol="http" bindingInformation="*:3000:localhost" />
  </bindings>
</site>
```

   D) Add "binding" directives under "bindings." My changed configs look like this.
```xml
<site name="RemoteAccess.web" id="17">
  <application path="/" applicationPool="Clr4IntegratedAppPool">
     <virtualDirectory path="/" physicalPath="C:\Users\Justin Walker\Documents\Visual Studio 2013\Projects\Remote Access\RemoteAccess.Web" />
  </application>
  <bindings>
     <binding protocol="http" bindingInformation="*:3000:localhost" />
     <binding protocol="http" bindingInformation="*:3000:pc-hostname" />
     <binding protocol="http" bindingInformation="*:3000:10.0.1.10" />
  </bindings>
</site>
```
