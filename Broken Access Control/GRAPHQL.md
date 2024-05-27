Query language in a form of rest request 


https://www.yeswehack.com/learn-bug-bounty/how-exploit-graphql-endpoint-bug-bounty

https://github.com/danielmiessler/SecLists/blob/fe2aa9e7b04b98d94432320d09b5987f39a17de8/Discovery/Web-Content/graphql.txt


The principal problem in GraphQL is: by design, you don’t have any control access system, developer has to write “resolvers” which will map the data to the queries for the database of his choice.


This is why the most commons issues which happens in Query are authorization logic flaw like Improper Access Control and IDOR.


tools:
- Clairvoyance : [https://github.com/nikitastupin/clairvoyance](https://github.com/nikitastupin/clairvoyance)
- GraphQLmap : [https://github.com/swisskyrepo/GraphQLmap](https://github.com/swisskyrepo/GraphQLmap)

https://www.yeswehack.com/learn-bug-bounty/how-exploit-graphql-endpoint-bug-bounty


https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/graphql