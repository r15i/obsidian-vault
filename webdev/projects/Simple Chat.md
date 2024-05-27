semplice chat, le persone si connettono con un username randomico e possono scrivere quello che vogliono su questa parete
- abbiamo un filtro per poter vedere solo i messaggiscritti da un utente o una lista di utenti(è solamente un filtro, se viene aggiornato non mostrerà roba delpassato)
- abbiamo un tracciamento di utenti che traccia in base a quanto una persona  sta sul sito la grandezza del suo nome sopra


![[Immagine WhatsApp 2024-01-19 ore 20.27.21_f02b6490.jpg]]


# Stile 
material design 3
https://github.com/material-components/material-web/blob/main/docs/quick-start.md

```shell
npm install @material/web
npm install svelte-materialify
```

list of components https://github.com/material-components/material-web/tree/main/docs/components


- lists  https://github.com/material-components/material-web/blob/main/docs/components/list.md#api


# {}
In Svelte, `{}` is used for reactive statements and expressions. When you wrap an expression or statement in curly braces `{}`, Svelte treats it as reactive, meaning it will automatically update the DOM whenever the value of the expression changes.




pocket base 


default collaction for the users

- create users and messages schema in pocket base: make the objects and link it with id like in a relational database
- create new record to test
- create api rules for frontend application are based on each collection of data![[Pasted image 20240201140841.png]]
- adds a rule for the id 





- pocket base javascript sdk 
		for user autentication and for the communication with the db 
		
```
npm i pocketbase
```
