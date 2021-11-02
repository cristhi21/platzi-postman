# Curso de Postman
Instruido por: Eduardo Álvarez



## 2. Estudiando el protocolo HTTP, verbos y status

GET: Traer informacion de un servidor, datos, recursos
HEAD: No nos retorna informacion, pero el resto es igual al Get. 
POST: Enviar informacion hacia el server, creacion de recursos, etc.
PUT: Actualizar info de un reccurso, completamente.
PATCH: Se usa para actualizar una parte del recurso no todo., si queremos actualizar todo el recurso se usa PUT
DELETE: Elimina un recurso.


### HTTP STATUS CODE:
Descrirben el estado de la peticion hecha al server

1xx : La peticion fue recibida y el servidor la esta trabajando.

2xx : Peticion fue recibida, aceptada y precesada correctamente.

3xx: Indica que hay acciones adicionales que se deben de hacer, por lo general se utilizan en las redirecciones.

4xx: Errores del cliente. Indica que se realiza una solicitud errónea.

5xx: Errores del servidor. Indica que el servidor presenta un error.

Errores más comunes

200: La petición fue correcta.
201: Es el estado cuando la solicitud Post fue correcta.
204: La solicitud fue procesada correctamente pero no devuelve información.
400: Bad request, la solicitud no es correcta.
401: Authorized, indica que se debe de realizar una autenticación antes de realizar una petición.
403: Forbidden: No se tiene acceso al recurso aunque se esté autenticado.
404: Not Found, el recurso no fue encontrado.
500: Internal Server Error, el servidor indica que la solicitud no pudo ser procesada.

- [Curso de API REST](https://platzi.com/clases/api-rest/)
- [HTTP Status Messages](https://www.w3schools.com/tags/ref_httpmessages.asp)
- [Repositorio github](https://github.com/platzi/postman-course)






## 3. Estructuras de las URLs


En un API es importante tener bien estructuradas las rutas por las cuales se usarán cada uno de los endpoints que contiene. Antes de entrar de lleno a explicar el API con el que trabajaremos en este curso veamos unos conceptos muy importantes a la hora de trabajar con APIs.

Recurso
Es la instancia o la representación de un objeto o la representación de algo, tiene datos y operaciones asociadas a él. Por ejemplo: course, material y video son recursos que tenemos disponibles en el API con la que trabajaremos y podemos realizar operaciones sobre ellos: crear, actualizar y eliminar.

Colecciones
Es un conjunto de recursos, por ejemplo: courses es una colección de course.

URL
(Uniform Resource Locator) es la ruta en la cual puede ser ubicado un recurso y ejecutar las operaciones sobre él.

CRUD
Siglas que hacen referencia a las operaciones básicas que se pueden ejecutar sobre un recurso:

C: Create (crear)
R: Read (leer)
U: Update (actualizar)
D: Delete (eliminar)
Endpoints
Es el punto final de la comunicación con un ente, en este caso, un endpoint está asociado a una URL y a las operaciones que podemos ejecutar. Este término es muy utilizado en las APIs.

Los endpoint definen operaciones que se quieren ejecutar sobre un recurso. Por ejemplo: si queremos un conjunto de operaciones CRUD sobre Cursos podríamos crear los siguientes endpoints:

/get-all-courses : para obtener una colección de Cursos.
/add-new-course: para crear un nuevo recurso de Cursos.
/delete-all-courses: para eliminar todos los Cursos.
Y así sucesivamente. Pero, esto implicaría un problema. El API puede llenarse de endpoints que ejecutan una sola operación, esto no es escalable, significa que si por ejemplo el recurso Cursos pasa a llamarse Clases habría que actualizar absolutamente todas las URLs y asegurarse de ello puede convertirse en un dolor de cabeza.

Entonces, ¿cuál es la buena práctica en este caso?

Como lo vimos en la clase pasada, el protocolo HTTP especifica una serie de verbos que indican acciones. Lo ideal es que la operación que se ejecute sobre un recurso se obtenga a través del verbo HTTP de la petición y no que esté definido en el endpoint. Por ejemplo:

/courses: Dependiendo del verbo HTTP se ejecutará una operación en particular. Quedaría así:
GET /courses: trae la colección de Cursos.
POST /courses: crea un nuevo recurso de Cursos.
DELETE /courses: elimina todos los cursos.
De esta manera queda mucho más organizado un API. Pero, qué pasa si queremos traer no una colección de cursos como en los casos anteriores, sino un recurso en específico.

Por lo general cada recurso tiene un identificador único, un ID, es con esto que llamaremos a un endpoint para que nos retorne la información del recurso. Por ejemplo:

GET /courses/2/: vemos que acá se le está pasando algo que en los endpoints anteriores no veíamos, es el número 2, ese es el identificador único, de esta manera el API sabe que tiene que buscar el curso con ID 2 y retornarlo.
Así sucesivamente con cada uno de los verbos, por ejemplo: casi nunca se hace una eliminación en masa en un API, como el ejemplo que tenemos más arriba donde se eliminan todos los cursos. Lo ideal es que se elimine un recurso individualmente y no una colección, igualmente pasa con la actualización.

Recursos anidados
Hay veces en las que un recurso depende de otro recurso, por ejemplo, comentarios depende de materiales; usualmente en los APIs las anidaciones se hacen hasta dos niveles, es decir:

materials/1/comments: estos son dos niveles
materials/1/comments/2/answers/: son tres niveles, ahí lo ideal sería entonces separar el endpoint de comentarios y ejecutar comments/2/answers/
Nuestro API
Ya he dado algunos spoilers sobre lo que nuestro API hace, es un clon de lo que Platzi es, una plataforma es donde tenemos Cursos, Materiales, Videos y Comentarios. El API es sencillo y es una prueba que utilizamos en este curso para explorar toda las capacidades que nos ofrece Postman para trabajar con ellos.

Una convención que se usa a la hora de documentar APIs es abstraer el endpoint de la URL del sitio al cual vamos a hacer la petición, puesto que esto al final es redundante de escribir, es decir, usualmente escribimos únicamente /api-token-auth/ en vez de [http://mistioweb.com/api-token-auth/](http://mistioweb.com/api-token-auth/).

Los endpoints que tenemos:

- /api-token-auth/
- /courses
- /courses/:id/
- /courses/:id/upload_badge/
- /materials/
- /materials/:id/
- /materials/:id/comments/
- /comments/
- /comments/:id/
- /comments/:id/like/
- /comments/:id/dislike/


Lecturas Recomendadas

- [Arquitecturas REST y sus niveles](https://www.arquitecturajava.com/arquitecturas-rest-y-sus-niveles/)
- [Buenas prácticas para el diseño de un API REST](https://platzi.com/clases/1461-django-avanzado/17199-buenas-practicas-para-el-diseno-de-un-api-rest/)




## 4. Estructuras de las URLs





## 5. Cómo ejecutar la API




## 6. Llamados a un API con GET: llamado de listas y detalles de objetos

GET= Te entrega Body y cabecera
HEAD = Te entrega exclusivamente la cabecera de la peticion

###  API Publicas
- [Rick and Morty Api](https://rickandmortyapi.com/api/character/)
- [Rick and Morty Api Documentacion](https://rickandmortyapi.com/documentation/)
- [Public APIs GitHub](https://github.com/public-apis/public-apis)
- [Star Wars API](https://pipedream.com/apps/swapi)
- [Poke Api](https://pokeapi.co/)


- [Curso Gratis de Programación Básica](https://platzi.com/clases/programacion-basica/)



## 7. Llamados a un API con GET: parámetros en la URL

- page_size=1             // Cantidad de results por pagina
- page=2                  // Numero de pagina
- ordering=-ranking       // ranking de menor a mayor y -ranking de mayor a menor
- begin_date=2019-11-23   // fecha



## 8. Llamamos a un API con el método post

Autenticacion por Token

Luego hacer uso de POST




## 9. Llamados a un API con el método post utilizando Form Data

A veces necesitamos hacer usar POST sin enviar algo en el body, solo con la URL
Ej: Dar like o Dislike

URL:
- [http://localhost:8000/api/comments/1/like](http://localhost:8000/api/comments/1/like)
- [http://localhost:8000/api/comments/1/dislike](http://localhost:8000/api/comments/1/dislike)

HEADER
Authorization	Token ......

El formato JSON no es el unico formato que tenemos para enviar datos al servidor.
hay otros 2

Body > raw > JSON

Body > raw > x-www-form-urlencoded

Funciona de una forma similar 

### Consola de Postman: Observar como se envia la estructura de la llamada

Body > raw > form-data


## 10. Llamados a un API con el método PUT


OPTIONS: trae informacion relevante sobre un endpoint
PUT: Actuaiza toda la instancia
PATCH: Actualiza una parte de la instancia

¿A traves de los metodos PUT y PATCH se puede enviar informacion con form-data?
Respuesta: Si.

Hay diferencia entre el uso de POST Y PUT y esta no radica en que POST cre y PUT actualiza. Sino en que PUT debe emplearse para crear o reemplazar un recurso(que se incluye en el cuerpo de la petición) en una URL conocida.

PUT a la URL: myServer.com/user/1134

Crea o reemplaza el usuario con ID 1134. Exclusivamente ese. Si queremos crear un usuario nuevo, sin saber su ID, la operación correcta sería POST:

POST a la URL: myServer.com/user

###  HTTP: diferencia entre POST y PUT
[HTTP: diferencia entre POST y PUT](https://notasjs.blogspot.com/2013/07/http-diferencia-entre-post-y-put.html)



## 11. Llamados a un API con el método DELETE


La URL es la misma, lo unico que cambia de un Requset a otro es el verbo 

status: 204. (No content)



## 12. Optimización de environment de postman y configuración de la colección


Environment(Entorno): Hace referencia a un contexto o grupo de valores que se puden usar a traves de enpoints. 
Los enviroments contienen variables.

Pensar en los valores transversales a los endpoints.

Lo normal es crear entornos distintos por cada API.

las variables de los environments tambien se pueden enviar en los headers de los endpoints.

Ej: Authorization. podemos enviar el Token que generamos para autenticarnos

### Variables de envoronments:

{{api_url}}
{{token}}

Una collection: es como una carpeta|folder. sirve para crear una documentacion con postman

Se puede crear una collection dentro de otra.

Se puede usar formato markdown para la descripcion de las colecciones

###  Markdown
https://markdownlivepreview.com/

### Markdown in API Documentation
https://documenter.getpostman.com/view/33232/markdown-in-api-documentation/JsGc




## 13. Agregar ejemplos de responses y descripción de endpoints

DOCUMENTACION DE LOS ENDPOINT


### AGREGAR EJEMPLOS DE RESPONSES

1. Hacer una request a un endpoint
2. Save response
3. Darle un nombre
4. Observar el body y los Header

Tambien podemos especificar el status
Podemos guardar un request Success

Tambien podemos hacer fallar la request para que salga un error 400


### DOCUMENTAR EL ENDPOINT
En la descripcion del endpoint podemos guardar lo que necesitemos en formato Markdown

EJ: This is the description for Comments Creation

Request: 
- `content`: `String` especify the content of a comment
- `matreial`: `Int` especify the material

En esta clase aprendimos a guardar endpoints de respuestas en especifico 201 Creacion Exitosa
400 Mala petición

Tambien creamos la descripcion del API

###  Editor Markdown
https://pandao.github.io/editor.md/en.html

###  Swagger
https://swagger.io/

###  Creando mock server con Postman
https://platzi.com/tutoriales/1765-postman/4882-creando-mock-server-con-postman/

>Nota: Investigar sobre la creacion de un Mock Server

## 14. Guardar el token del login con una prueba automática

Automatizacion de procesos en postman
Guardar una variable de un response en nuestro entorno

### Ciclo de vida de cada Request que hacemos en postman
1. Prerequest: Calcular una variable o algo antes de enviar al request
2. REQUEST: Llamar al API
3. RESPONSE: Respuesta
4. Test (Pruebas del response)

Ejecutar codigo antes de hacer un llamado a la API usando el pre-request Script.
Asi guardamos un valor dentro de una variable del entorno antes de su ejecucion.

### Al parecer es lo mismo
pm.environment.set("name_var", value)
postman.setEnvironmentVariable("name_var", value)


Ej: Guardar variable today en el envoronment:

pm.environment.set("today", new Date().toISOString())

Si quiero guardar una variable en el entorno despues de la ejecucion de un endpoint
debo hacerlo en el Test, ya que según el ciclo de vida es lo que me llega luego de hacer un response

Esto es util para las autenticaciones

var json = JSON.parse(responseBody);
postman.setEnvironment("token", `Token ${json.token}`);



### Escuela de JavaScript
https://platzi.com/escuela-javascript/

### Scripting in Postman
https://learning.postman.com/docs/writing-scripts/intro-to-scripts/





## 15. Creación de Pruebas para endpoints

1. poner endpoint

var json = JSON.parse(responseBody);
postman.setEnvironment("token", `Token ${json.token}`);

Los test tienen snippets

pm.test("Successfull POST Request", function() {
    pm.expect(pm.response.code).to.be.oneOf([201,202]);
})


### Test script examples
https://learning.postman.com/docs/writing-scripts/script-references/test-examples/

### Tutorial
https://www.guru99.com/postman-tutorial.html

### BDD
https://www.chaijs.com/api/bdd/



## 16. Publicar Documentación


1. Documentar todos los end-point y collections usando formato md
2. Publish Doc



## 17. Cierre del curso


### Postman Beginner's Course - API Testing
https://www.youtube.com/watch?v=VywxIQ2ZXw4

### Curso de API REST
https://platzi.com/clases/api-rest/

### Curso de Backend con Node.js
https://platzi.com/clases/backend-nodejs/

### Curso de Unit Testing con Jest en React
https://platzi.com/clases/jest/




## Preguntas y respuestas


1. El protocolo HTTP es el utilizado por la web para transferir datos:
Sí

2. El método GET es el utilizado para:
Traer datos de una colección o recurso

3. La documentación que Postman genera se alimenta de:
La coleccion de Postman
La documentacion que se escribe en el endpoint
Los ejemplos de response que se guardan en el endpoint

4. Para subir una imagen a través de POST utilizo:
FormData

5. ¿Qué me permite una colección en Postman?
Configurar los datos que se enviarán a la API,
Documentar los endpoints que se utilizan
Organizar los endpoints del API

6. ¿Cómo es la URL para traer la página 3 de la lista de cursos?
`/courses/?page=3`

7. En qué casos se utiliza PUT y PATCH:
PUT para actualizar todo el recurso y PATCH para hacer una actualización parcial

8. El status HTTP esperado cuando se hace una petición POST para crear un comentario en el API del curso es:
201

9. A través del environment puedo almacenar valores para ser utilizados en varias peticiones.
Sí

10. Para guardar la variable date en el environment global en Postman escribo:
`pm.globals.set("date", "the value");`

11. ¿Es JSON el único formato que acepta POST para crear un recurso?
No

12. En los ejemplos de responses en Postman puedo:
Guardar un response por cada status que me retorne el API

13. El método DELETE en el API del curso se utiliza para:
Eliminar un recurso

14. El ciclo de vida de una petición en Postman es:
prerequest, request, response, tests

15. ¿El lenguaje de pruebas que acepta Postman es?
Javascript