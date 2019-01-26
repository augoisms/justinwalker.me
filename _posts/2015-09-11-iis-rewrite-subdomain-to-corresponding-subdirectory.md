---
layout: post
title: IIS - Rewrite Subdomain To Corresponding Subdirectory
date: '2015-09-11 20:46:42'
tags:
- iis
---

At work we have a website setup to showcase some of our work. We only ever send people directly to a specific example and the method we employed was to just put each web project in a subdirectory of the root (e.g. `example.com/great-project`). This can be problematic, especially for single pages apps, where the code is expecting the site to be located at the root. To avoid having to edit code I set up a new website on azure with a wildcard subdomain that points to a corresponding subdirectory.

The following rule will point any subdomain to a corresponding directory. So, `demo.example.com` will point to `example.com/demo`. Make sure than you have a `CNAME` record of `*` that points to your root domain.

```
<?xml version="1.0"?>
<configuration>
  <system.webServer>
    <rewrite>
      <rules>
  		<rule name="Redirect subdomain" enabled="true" stopProcessing="true">
  			<match url="^(.*)$"/>
  			<conditions>
  				<add input="{HTTP_HOST}" pattern="^(.*)\.example\.com$"/>
  			</conditions>
  			<action type="Rewrite" url="{C:1}/{R:0}"/>
  		</rule>
      </rules>
    </rewrite>
  </system.webServer>
</configuration>
```

--------
References:
- [http://azure.microsoft.com/en-us/blog/azure-websites-and-wildcard-domains](http://azure.microsoft.com/en-us/blog/azure-websites-and-wildcard-domains/)