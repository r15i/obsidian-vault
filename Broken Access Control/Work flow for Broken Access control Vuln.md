
useful giveaway 
https://cwe.mitre.org/data/definitions/204.html
https://cwe.mitre.org/data/definitions/307.html
https://cwe.mitre.org/data/definitions/798.html

# 1. Test proper login 

Make sure to have proper authentication: 
without any logins, do not allow access to resources that an unauthorized user should not have access to.Deny by default is generally a good approach, unless some resources are marked for public access.


##### weak password policy 
allow to change password or use weak passwords 
discloses password or tokens in the url 
graphQL queries allow for many authentication attempts in a single request 
lacking of authentication for sensitive requests

### credential stuffing 
allowing to try multiple combination of passwords and usernames (usually from data breaches)


# incremental or predictable tokens 

easily predicted or guessable tokens or calculated (**we may use nerural network here to predict tokens**)
- insufficient token randomness(entropy)

## password reset and multifactor autentication 
can be the fault 










# 2. Proper cookies and token handling 
Make sure that the session management is done properly: 
cookies and JWT tokens are secure enough and their absence doesn’t gives back pages accessible to authenticated users

Jason web token ()


# 3.  Make sure there is no bruteforce capability for the session 

Check that the cookies and the tokens are not bruteforceble

Make sure that the session management is done properly: cookies and JWT tokens are secure enough and their absence doesn’t gives back pages accessible to authenticated users

# 4. Never trust user input 
well test the user input 
check how the user input is translated into parameters


EXAMPLE:
An exposed directory listing resulting in access to sensitive files (.htpasswd, .git, .ssh, aws creds, app code, …) 
and passwords for instance would fit in deny by default point, 

whereas a JWT token vulnerable to kid claim injection would fit in the 3rd point as well as the 5th point.

