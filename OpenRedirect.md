## Everything about OpenRedirect

Considered as a low vulnerability and not that common.  
Used for phishing attacks mainly as users might not read the entire url and http://website.com/example.php?url=evil.com doesnt look at bad!  

URL parameter can be  

redirect=  
r=  
url=  
redirect_to  
etc  

### Methods that can be used to hide 'evil.com' in url

1) Hexadecimal coding it   
2) Special domain name could also be used  

example -   

http://mystore.myshopify.com/account/login?checkout_url= .attacker.com  


they would have been redirected to the URL:  
http://mystore.myshopify.com.attacker.com  

which actually isn’t a Shopify domain anymore because it ends in .attacker.com. DNS  
lookups use the right-most domain label, .attacker.com  

Here domain .attacker.com is owned by attacker and that redirects user to attacker.com.  

3) Often websites use outside services like Zendesk (in case of HackerOne) and these are landing pages between redirects, read WebHacking   handbook.

4) Redirect via javascript  

https://example.com/index.php?redirecturl=javascript:alert(document.domain)


## Redirects response code in HTTP requests  

300-400  

301 - Moved permanently  
302 - Found  
303 - See other  
307 - Temporary redirect  
308 - Permanent Redirect  

### Consequences

1) Phishing
2) XSS - if redirect allows use of data or javascript
3) SSRF - maybe used to evade ssrf filters
4) [CRLF](https://www.acunetix.com/websitesecurity/crlf-injection/) - If redirect parameter allows line break, try to perform response header splitting


Long blog - https://www.neuralegion.com/blog/open-redirect-vulnerabilities/