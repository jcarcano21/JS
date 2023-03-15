# REST (Representational State Transfer)

És un estil arquitectònic utilitzat per dissenyar *aplicacions web*. És un conjunt de principis i restriccions que s'utilitzen per construir sistemes distribuïts, en què els recursos són identificats per URI (Uniform Resource Identifier) ​​i són manipulats mitjançant mètodes HTTP estàndard (*GET*, *POST*, *PUT*, *DELET*, entre d'altres).
És basa en la separació clara de responsabilitats entre el client i el servidor. El client realitza sol·licituds HTTP per obtenir o manipular els recursos, mentre que el servidor proporciona les respostes a aquestes sol·licituds en un format estàndard, com ara ***JSON***.
L'arquitectura REST en si mateixa no està escrita en un llenguatge de programació específic, ja que és un conjunt de principis i restriccions arquitectòniques per al disseny d'APIs web.

No obstant això, en implementar una API REST, és comú utilitzar llenguatges de programació com Java, Python, Ruby, Node.js, entre d'altres.
# Punts principals:

1.  *Identificación de recursos*: cada recurso debe ser identificado de manera única mediante una URI.

2. *Manipulació de recursos a través de representacions*: els recursos es manipulen mitjançant la transferència de representacions entre el client i el servidor.

3. *Missatges autodescriptius*: cada missatge ha de contenir tota la informació necessària per processar-lo.

4. Ús de mètodes HTTP estàndard: els mètodes HTTP estàndard s'utilitzen per a la manipulació dels recursos, com ara ***GET*** per obtenir un recurs, ***POST*** per crear-ne un de nou, ***PUT*** per actualitzar-ne un de existent i *** DELETE*** per eliminar un recurs. 

5. *Ús d'hipertext*: els recursos han d'incloure hiperenllaços que permetin la navegació a altres recursos relacionats. 

##   Recursos i URIs

En la arquitectura REST, los recursos son los objetos o datos que se pueden acceder a través de la web. Cada recurso se identifica mediante una **URI** (*Uniform Resource Identifier*), que es una cadena de caracteres que identifica de manera única el recurso.

L'estructura d'una *URI* a *REST* és important, ja que permet que els clients accedeixin als recursos de manera clara i coherent. Una URI REST típica consta de tres parts principals:

-  Les URI rebran noms que no han d'implicar una acció, és a dir, cal evitar col·locar-hi verbs. Això és perquè es posa èmfasi en els substantius:
>http://...../imatges/12/esborrar INCORRECTE
>http://...../imatges/12 CORRECTE
- Han de ser úniques, no cal tenir més d'una URI per identificar un mateix recurs.
- Han de ser independents del format, és a dir, no ha de representar cap extensió:
>http://...../usuari/231/imatges/231 INCORRECTE
>http://...../usuari/231/imatges/12 CORRECTE 
- Han de mantenir una jerarquia lògica. La jerarquia és el criteri pel qual sordena els elements. Al següent exemple s'aprecia la diferència:
>http://...../imatges/231/usuari/12 INCORRECTE
>http://...../usuari/231/imatges/12 CORRECTE
>
>*En el cas incorrecte es podria llegir com a «foto 12 té usuari 231», situació poc lògica. En canvi en el cas correcte, podríem llegir-lo com a «usuari 231 té foto 12», cosa que sona més lògica.*
- Els filtratges d'informació d'un recurs no es fan a l'URI:
>http://...../imatges/data/octubre INCORRECTE
>http://...../imatges?data=octubre CORRECTE
- Exemple de codi:
>Obtenir totes les tasques:
```javascript
app.get('/tareas', (req, res) => {
	res.json(tareas);
});
```

## Metodes

A continuació es presenten alguns exemples de com s'utilitzen els mètodes *HTTP* a l'arquitectura *REST*:

- Mètode **GET**:
	- Serveix per recuperar informació sobre un recurs específic.
	- Un exemple, seria obtenir usuaris d'una col·lecció o amb la id = 1:
```javascript
	GET /users
```
```javascript
	GET /users/1
```
- Mètode **POST**:
	- Serveix per crear nous recursos.
	- Un exemple seria, afegir un nou usuari a la col·lecció:
```javascript
	POST /users
	Body: {
	    "name": "Juan",
	    "age": 30
	}
```
- Mètode **PUT**:
	- Serverix per actualizar recursos.
	- Un exemple seria, per actualitzar un usuari específic amb ID = 1:
```javascript
	PUT /users/1
	Body: {
	    "name": "Juan Carlos",
	    "age": 31
	}
```
- Mètode **DELETE**:
	- Serveix per eliminar recursos.
	- Un exemple seria, per eliminar un usuari específic amb ID = 1:
```javascript
	DELETE /users/1
```
- Mètode **PATCH**:
	- El mètode PATCH s'utilitza quan volem actualitzar un camp o propietat d'un recurs sense haver-lo de reemplaçar sencer.
	- Aquí hi ha un exemple de sol·licitud HTTP PATCH per actualitzar parcialment un recurs:
```javascript
	PATCH /usuarios/123 HTTP/1.1
	Host: ejemplo.com
	Content-Type: application/json
	{
	  "nombre": "Juan",
	  "apellido": "Pérez",
	  "edad": 30
	}
```
- Mètode **HEAD**:
	- El mètode HEAD s'utilitza per verificar si un recurs està disponible, per recuperar informació de la capçalera o la darrera data de modificació del recurs.
	- Un exemple de sol·licitud HTTP HEAD per a un recurs determinat:
```javascript
	HEAD /example HTTP/1.1
	Host: example.com
```
- Mètode **OPTIONS**:
	- El metode options serveix per informar el client sobre les opcions disponibles per interactuar amb el recurs
	- Un exemple de sol·licitud HTTP OPTIONS per a un recurs determinat:
```javascript
	OPTIONS /example HTTP/1.1
	Host: example.com
```
## Conclusió
En conclusió REST és una arquitectura de serveis web simple, escalable i flexible. En utilitzar els mètodes HTTP, facilita el desenvolupament de serveis web i la integració amb altres sistemes.  
És portàtil és a dir, permet una interoperabilitat fàcil entre diferents sistemes i dispositius, gràcies als recursos que s'identifiquen mitjançant URI i s'hi accedeix mitjançant els mètodes HTTP.  
En poder crear aplicacions distribuïdes (aplicació amb diferents components que s'executen en entorns separats), això permet una gran escalabilitat i redundància en cas de fallades en els components del sistema.  
En resum, és una arquitectura altament eficaç per la seva simplicitat, escalabilitat i flexibilitat.
