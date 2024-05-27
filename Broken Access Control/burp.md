ffor burp installation inside hackerone folder in tools burp 

![[Pasted image 20240504183115.png]]


### Dashboard

gives you an overview of the event log and scans you have run against your targets. The Dashboard is more useful in Burp Suite Pro than in CE because it will also display any issues detected during testing.
### Proxy 
The Proxy tab is where we will begin capturing requests and responses from your web browser and Postman. The proxy we set up will send any web traffic destined for your browser here. We will typically choose to forward or drop captured traffic until we find the targeted site that we want to interact with. From Proxy we will forward the request or response to other modules for interaction and tampering.

### Target 
In the Target tab, we can see a site’s map and manage the targets we intend to attack. You can also use this tab to configure the scope of your testing by selecting the Scope tab and including or excluding URLs.
Including URLs within scope will limit the URLs being attacked to only those you have authorization to attack


### The Intruder
tab is where we’ll perform fuzzing and brute-force attacks against web applications. Once you’ve captured an HTTP request, you can forward it to Intruder, where you can select the exact parts of the request that you want to replace with the payload of your choice before sending it to the server.

https://www.youtube.com/watch?v=mibKttwhbRk&ab_channel=InsiderPhD


Altering requests:

Any part of a captured HTTP request can be transformed into a variable, or attack position, by surrounding it with **§** symbols. Payloads can be anything from a wordlist to a set of numbers, symbols, and any other type of input that will help you test how an API provider will respond


Request example 

POST /example?p1=§p1val§&p2=§p2val§ HTTP/1.0
Cookie: c=§cval§
Content-Length: 17
p3=§p3val§&p4=§p4val§


**Example**:
![[Pasted image 20240504192748.png]]

Types of attacks :
- **Sniper**: it replaces the added attack position with a string provided from a single set of payloads. A sniper attack is limited to using a single payload, but it can have several attack positions
![[Pasted image 20240504193339.png]]

- **Battering ram**  is like the sniper attack in that it also uses one payload, but it will use that payload across all attack positions in a request. If you were testing for SQL injection across several input positions within a request, you could fuzz them all simultaneously with battering ram. 
- **Pitchfork** is used for testing multiple payload combinations at the same time. For example, if you have a list of leaked usernames and password combinations, you could use two payloads together to test whether any of the credentials were used with the application being tested. However, this attack doesn’t try out different combinations of payloads; it will only cycle through the payload sets like this: user1:pass1, user2:pass2, user3:pass3. 
- **Cluster bomb** will cycle through all possible combinations of the payloads provided. If you provide two usernames and three passwords, the payloads would be used in the following pairs: user1:pass1, user1:pass2, user1:pass3, user2:pass1, user2:pass2, user2:pass3

## Main usage of the intruder:
**Intruder should help you find API vulnerabilities such as broken object level authorization, excessive data exposure, broken authentication, broken function level authorization, mass assignment, injection, and improper assets management**


### The Repeater 
is a module that lets you make hands-on adjustments to HTTP requests, send them to the targeted web server, and analyze the content of the HTTP response.


The **Repeater module is the best way to see how a web server** responds to a single request. This is useful for seeing what sort of response you can expect to get from an API before initiating an attack. It’s also helpful when you need to make minor changes to a request and want to see how the server responds.


### The Sequencer
tool will automatically send hundreds of requests and then perform an analysis of entropy to determine how random a given string is. We will primarily use this tool to analyze whether cookies, tokens, keys, and other parameters are actually random.


### Learn
is an awesome set of resources to help you learn how to use Burp Suite. This tab contains video tutorials, the Burp Suite Support Center, a guided tour of Burp’s features, and a link to the PortSwigger Web Security Academy. Definitely check these resources out if you are new to Burp! Under the Dashboard you can find the Burp Suite Pro Scanner. Scanner is Burp Suite Pro’s web application vulnerability scanner. It lets you automatically crawl web applications and scan for weaknesses.


### The Extender
is where we’ll obtain and use Burp Suite extensions. Burp has an app store that allows you to find add-ons to simplify web app testing. Many extensions require Burp Suite Pro, but we will make the most of the free extensions to turn Burp into an API hacking powerhouse.
