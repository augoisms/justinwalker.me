---
layout: post
title: Parse, PHP,  and cURL on Windows Azure
date: '2015-08-26 18:05:22'
---

I was recently trying to use [Parse's PHP SDK](https://github.com/ParsePlatform/parse-php-sdk) and was running into some issues when I deployed the project to Azure. Whenever I would attempt to run any of the Parse scripts I would get a `500 Internal Server Error`.

It turns out that Parse is using `cURL` which does not ship with it's own CA certificate bundle. To fix the problem I needed to specify a CA cert bundle for PHP's cURL. All the steps below can be accomplished in the Kudu interface which you can access at `[your-azure-site-name].scm.azurewebsites.net`.


**1. Create Custom php.ini**<br>

- In the Kudu console, click on the planet-looking icon.
- From there go in the config folder, and then in the PHP-5.5.18 folder (or whatever version you're using).
- Run `copy php.ini d:\home\site` to copy it to your site folder.
- Click the Home icon, and then go in the site folder to find your copy of php.ini.
- Edit the file. Add the following line:
```
curl.cainfo ="D:\home\site\ca-bundle.crt"
```

**2. Create applicationhost.xdt**

- While still at `D:\home\site\` create a new file.
```
echo temp > applicationhost.xdt
```
- Edit the file and paste in the following contents:
```
<?xml version="1.0"?> 
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform"> 
  <system.webServer> 
    <fastCgi>
      <application fullPath="D:\Program Files (x86)\PHP\v5.4\php-cgi.exe" xdt:Locator="Match(fullPath)">
        <environmentVariables>
          <environmentVariable name="PHPRC" xdt:Locator="Match(name)" value="d:\home\site\php.ini" xdt:Transform="SetAttributes(value)" />
        </environmentVariables>
      </application>
    </fastCgi>
  </system.webServer> 
</configuration>
```
- Make sure to change the php version if needed.

**3. Create ca-bundle.crt**

- While still at `D:\home\site\` create a new file.
```
echo temp > ca-bundle.crt
```
- Edit the file and paste the contents of `ca-bundle.crt` found here:<br>
[http://curl.haxx.se/docs/caextract.html](http://curl.haxx.se/docs/caextract.html)

**4. Restart the site**


-----
References

- [https://github.com/projectkudu/kudu/wiki/Xdt-transform-samples#using-a-custom-phpini](https://github.com/projectkudu/kudu/wiki/Xdt-transform-samples#using-a-custom-phpini)
- [http://blogs.msdn.com/b/azureossds/archive/2015/06/12/verify-peer-certificate-from-php-curl-for-azure-apps.aspx](http://blogs.msdn.com/b/azureossds/archive/2015/06/12/verify-peer-certificate-from-php-curl-for-azure-apps.aspx)
- [http://ea.tl/2012/02/02/windows-php-curl-ssl-certificate-problem.html](http://ea.tl/2012/02/02/windows-php-curl-ssl-certificate-problem.html)