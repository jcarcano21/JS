# **Tecnologia NODE i el framework EXPRESS**
## Node
Node.js és un entorn d'execució de JavaScript de codi obert i multiplataforma que es fa servir per desenvolupar aplicacions escalables del costat del servidor i de xarxa. Està basat en el motor dexecució JavaScript V8 de Google Chrome.

Altres tasques comunes de desenvolupament web no estan directament suportades pel mateix Node. Si vols afegir el maneig específic de diferents verbs HTTP (ex, GET, POST, DELETE, etc.).Es per això que podem escriure el codi nosaltres mateixos o utilitzar un framework web com Express.

Com instal·lar NODE.js:
### Windows:
>- Descarregarem el instalador de Node.js: https://nodejs.dev/en/download/ 
### Linux:

>- Anirem al terminal i farem: ***sudo apt install nodejs***
>- Seguidament farem: ***sudo apt install npm***
#### Per verificar la instalació farem:
>node -v  (nodejs -v a linux)
>npm -v
#### Exemple de Node per respondre a una petició HTTP:
```javascript
// Primer carregarem el mòdul HTTP
var http = require("http");
// Crearem el servidor HTTP i definirem el port en que estara la conexió
// Escoltarà qualsevol petició al port 8000
http.createServer(function(request, response) {
	// Es defineix la capçalera HTTP amb el estat 200(conexió correcte) i el tipus de contingut
   response.writeHead(200, {'Content-Type': 'text/plain'});

   // A response definirem la nostra resposta
   response.end('Missatge de prova\n');
}).listen(8000);

// Escriurem a la consola el servidor
console.log('Servidor en la url http://127.0.0.1:8000/');
```
## Express
Com instal·lar Express:
>- npm install express --save

Express és el framework web més popular de Node, i és la llibreria per a altres frameworks web de Node populars. Proporciona mecanismes per a:

- Escriptura per manejar peticions amb diferents verbs HTTP a diferents camins URL (rutes).
Integració amb motors de renderització de "vistes" per generar respostes mitjançant la introducció de dades a plantilles.
- Establir ajustaments d'aplicacions web com quin port utilitzar per connectar, i la localització de les plantilles que s'utilitzen per renderitzar la resposta.
- Afegir processament de peticions "middleware" addicionals, perquè les diferents aplicacions es comuniquin  entre si.

Express posseeix mètodes per especificar quina funció ha de ser anomenada depenent del verb HTTP usat a la petició (GET, POST ) i l'estructura de la URL ("ruta"). També teniu els mètodes per especificar quina plantilla ("view") o gestor de visualització utilitzar, on estan guardades les plantilles d'HTML que s'han d'utilitzar i com generar la visualització adequada per a cada cas. El middleware d'Express, també es pot utilitzar per afegir funcionalitats per a la gestió de cookies, sessions i usuaris, mitjançant l'ús de paràmetres, en els mètodes POST/GET. A més, es pot utilitzar qualsevol sistema de treball amb bases de dades, que sigui suportat per Node.

Exemple de Express:
```javascript
// mitjançant l'ordre require()) el mòdul Express i creen una aplicació Express
var express = require('express');
var app = express();
// mostren una definició de ruta que es trucarà quan es rebi una petició HTTP GET
// amb una adreça ('/') relativa al directori arrel.
app.get('/', function(req, res) {
  res.send('text de exemple');
});
//  crea el servidor, escoltant el port 3000 i imprimeix un comentari a la consola. 
// Quan s'està executant el servidor, és possible anar fins a l'adreça localhost:3000 
// en un navegador, i veure com el servidor d'aquest exemple torna el missatge de resposta.
app.listen(3000, function() {
  console.log('Exemple de aplicació, escoltant al port 3000');
});
```
### Mètode GET
``
El mètode get es realitza de la manera següent, el mètode rep com a primer paràmetre la ruta del GET i com a segon paràmetre un on torna una resposta, generalment una pàgina web. Però en aquest cas només es va obtenir un string.

```javascript
aplicació.obtenir(
    '/',
    (sol·licitud, resposta) => {
        resposta.send('pàgina principal')
    }
);
```
### Mètode POST
El mètode post es realitza de la següent forma, el mètode rep com a primer paràmetre la ruta del POST i com a segon paràmetre els paràmetres del body ,i es finalitza enviant un missatge a l'emissor del POST.
```javascript
app.post('/', function (req, res) {
    var user_name = req.body.user;
    var password = req.body.password;
    console.log("User name = " + user_name + ", password is " + password);
    res.end("yes");
});
```
