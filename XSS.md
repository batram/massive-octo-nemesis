Cross Site Scripting (XSS)
==========================

> Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted web sites.
>
> -- <cite>https://www.owasp.org/index.php/Cross-site_Scripting_%28XSS%29</cite>


In Flash there are two ways to execute JavaScript that are commonly used and can lead to security problems.
Flash also has limited capablity to display content that is formatted in HTML.

ExternalInterface 
-----------------
>  The ExternalInterface class is an application programming interface that enables straightforward communication between ActionScript and the SWF container– for example, an HTML page with JavaScript or a desktop application that uses Flash Player to display a SWF file. 
>
> -- <cite>http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/external/ExternalInterface.html</cite>


<b>Example:</b>

ActionScript3-Source: 
```as3
ExternalInterface.call("confirm", loaderInfo.parameters.test);
```

FlashVars:
```
test=\"))}finally{confirm(/moin/)}//
```

resulting JavaScript:
```javascript
try { __flash__toXML(confirm("\\"))}finally{confirm(/moin/)}//")) ; } catch (e) { "<undefined/>"; }
```


javascript-URL
--------------
ActionScript2-Source: 
```ActionScript
getURL(clickTag, "_self");
```
