
# Web Services

"1. Descargue proyecto (02-JakartaEE-XML) donde está implementado el web service visto en clases. Provisione el servidor, deploye el código y analice los logs del servidor en busca de la url del wsdl asociado al servicio."

Tras haber descargado el práctico del [repositorio del profe](https://github.com/gabrielaramburu/TallerJakartaEE) me dispongo a correr el servidor y API proporcionada por el profe, para esto tuve que tirar:
```Bash
mvn install wildfly:dev
```
en la carpeta de proyecto: *021-JakartaEE-XML* porqué el servidor que tengo configurado en mi Eclipse no estába levantando bien la API, tras esto me dirijo a la dirección del *wsdl*
 que me indica el servidor cuando lo levanto.
 ![/Archivos/Pasted%20image%2020240406204645.png]
Este mismo se encuentra en http://localhost:8080/021-JakartaEE-XML/PagoSOAP?wsdl como índica la imagen arriba

---
"3) Instale aplicación SoapUI (client web service), realice y ejecute, una batería de test unitarios de dicho servicio. Analice los datos devueltos."

Se hace la instalación del SoapUI para linux
![[Pasted image 20240414190651.png]]


Se obtienen los pagos utilizando SoapUI:
![[Pasted image 20240414191106.png]]


Se realiza un pago nuevo:
![[Pasted image 20240414191246.png]]


Y se vuelve a revisar los pagos:
![[Pasted image 20240414191316.png]]
Se puede observar como el pago 3 es el que se acaba de realizar utilizando soapUI


# RESTful
"1. Descargue proyecto donde está implementado el servicio RESTful (02-JakartaRESTful). Provisione el servidor y deploye el código."

Se descarga el repositorio y despliega la API RESTful proporcionada utilizando el servidor WildFly previamente configurado en Eclipse. Tras esto se ejecutan los test unitarios.

Test unitario de RESTful número 1:
![[Pasted image 20240406213556.png]]

Test unitario de RESTful número 2:
![[Pasted image 20240406213803.png]]


Además de los test provistos, se hace uso de curl para probar el correcto funcionamiento de la API:

- utilizando cliente RESTful:
![[Pasted image 20240406214032.png]]

- utilizando cliente RCP:
![[Pasted image 20240406214204.png]]

---

"07) Instale aplicación Postman y cree una test unitario que para invocar los servicios RESTful"

Utilizando Postman se prueban los servicios provistos por la API RESTful:
![[Pasted image 20240406215449.png]]

y ahora para el cliente RCP:
![[Pasted image 20240406215546.png]]

---

"10)  Modifique la API RESTful para que ofrezca un método que dado un nombre de un cliente, devuelve si existe o no."

Se implementa la función (código se encuentra en este repositorio con su respectivo test unitario) y se prueba la misma con el cliente RESTful:
![[Pasted image 20240406222732.png]]

Cuando el cliente si existe:
![[Pasted image 20240406222821.png]]



Se vuelve a checkear la funcionalidad, esta vez con cliente RPC:
![[Pasted image 20240406223952.png]]


Cuando el cliente si existe:
![[Pasted image 20240406224041.png]]


# Swagger
"2) Lanze el servidor y verifique que la ulr [http://localhost:8080/02_jakartaRESTful_swagger/api/openapi.json](http://localhost:8080/02_jakartaRESTful_swagger/api/openapi.json) devuelve información sobre los servicios deployados."

Se descarga y deploya el repositorio "02-JakartaEE-RESTful-Swagger" utilizando 
```Bash
mvn install wildfly:dev
```
tras esto se verifica la URL proporcionada por OpenAPI:
![[Pasted image 20240406225829.png]]

---

"1. Invoque la página de documentación de swagger: [http://localhost:8080/02_jakartaRESTful_swagger/swagger.html](http://localhost:8080/02_jakartaRESTful_swagger/swagger.html)"

También se prueba la URL en donde OpenAPI prepara una página detallando todos los servicios provistos por nuestra API:
![[Pasted image 20240406230210.png]]

# RESTful API

Siguiendo el diagrama de modelo dominio, se realiza la API con las 2 clases, Empleado y Tarea, que son manejados por la implementación de empleadoService, el cual es nuestra capa de aplicaciones con los casos de uso correspondiente.

Y por ultimo se testean las funcionalidades del mismo haciendo uso de de los endpoints provistos por la clase Test.

Aquí se aprecia la estructura del proyecto
![[Pasted image 20240414175547.png]]


Procedo a demostrar el funcionamiento de todas las funciones que se pidierón en la letra del ejercicio.

### Agregar Empleado

Aquí está la implementación utilizada
![[Pasted image 20240414181255.png]]


Aquí la función y endpoints que se utilizan para comunicarse con el programa
![[Pasted image 20240414181351.png]]


Como lo vé el cliente:
![[Pasted image 20240414181510.png]]


Como aparece en el servidor:
![[Pasted image 20240414181538.png]]


### Asignar tarea a empleado

Aquí está la implementación utilizada
![[Pasted image 20240414181818.png]]


Aquí están tanto el endpoint como la función para comunicarse con el programa:
![[Pasted image 20240414182135.png]]


Aquí es como lo vé el usuario:
![[Pasted image 20240414182226.png]]


Como aparece en el servidor:
![[Pasted image 20240414182258.png]]

### Listar empleados

Aquí está la implementación utilizada:
![[Pasted image 20240414182459.png]]


Aquí las funciones y endpoints utilizados:
![[Pasted image 20240414182748.png]]


Como lo vé el usuario:
Cabe destacar que tuve que añadir un 2ndo empleado para demostrar correctamente el funcionamiento de listar empleados
![[Pasted image 20240414182932.png]]

Y aquí es como se visualiza en el servidor:
![[Pasted image 20240414183016.png]]

### Borrar empleado

Aquí está la implementación utilizada:
![[Pasted image 20240414183211.png]]


Aquí los endpoint y funciones utilizados para comunicarse con el servidor:
![[Pasted image 20240414183328.png]]


Aquí se prueba a borrar a un empleado con tareas ya asignadas:
![[Pasted image 20240414183519.png]]


Aquí se borra un empleado sin tareas:
![[Pasted image 20240414183635.png]]


y aquí es como se ve en el servidor:
![[Pasted image 20240414183723.png]]

### Listar información de un empleado en particular

Aquí está la implementación utilizada:
![[Pasted image 20240414183902.png]]


Aquí están las funciones y endpoints utilizados:
![[Pasted image 20240414183948.png]]


Aquí está como lo ve el usuario:
![[Pasted image 20240414184113.png]]

Aquí está como lo ve el usuario si intenta checkear un empleado que no existe:
![[Pasted image 20240414184213.png]]


Y aquí esta como se ve en el servidor:
![[Pasted image 20240414184331.png]]


### Listar las tareas de un empleado en particular

Aquí está la implementación utilizada:
![[Pasted image 20240414184448.png]]


Aquí la función y endpoints utilizados:
![[Pasted image 20240414184546.png]]


Aquí como lo vé el usuario:
Se añadió una tarea al usuario "Marta Habla" para poder ser capaces de demostrar la funcionalidad
![[Pasted image 20240414184747.png]]


Aquí como se ve en el servidor:
![[Pasted image 20240414184900.png]]
# Referencias
