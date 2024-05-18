
                                                                                  Consumiendo la API de spotify en angular (standalone components)


¡Hola! soy Elvis Johan Serna Vargas, y en esta ocasión te traigo un pequeño tutorial donde te explico como consumir la API de Spotify, a un nivel principiante. El objetivo de este tutorial es que aprendas a generar tokens utilizando la herramienta de Postman y que además aprendas a usar el modulo HttpClient que ofrece angular para realizar peticiones, en el tutorial he creado un pequeño clone de la pagina principal de la app móvil de Spotify, el proyecto lo puedes encontrar en GitHub, por si gustas clonarlo y tu mismo ir probando el tutorial paso por paso, como nota aclaratoria por fines rápidos, no mostrare como hice el maquetado y en algunos puntos no estuve tipiando todo (por rapidez) pero la idea es entender como funciona la api para traer los datos a nuestra app ( angular y ionic)

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/1743214c-66e7-4b99-834e-50ca053d9dd5)

                                                                                  
Comencemos!
Lo primero que hay que tomar en cuenta es que debes de tener una cuenta de Spotify, en mi caso es la uso personal, así que dirígete a la siguiente web e inicia sesión: https://developer.spotify.com/
Una vez que ya hayas iniciado sesión, aparecerá tu nombre en la esquina superior derecha, da clic a tu nombre y da clic en dashboard

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/59eee7c0-3d77-4aea-b331-a078373ee677)

 Para nosotros poder conectar nuestra aplicación, es necesario crear una app, en mi caso ya tengo una creada, pero para ti que vas a practicar, da clic en crear app:  

 ![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/3238b6df-57f8-4d15-af32-dedb0334cd45)

 Cuando le das clic en Create app, te aparecerá el siguiente formulario, solo es cuestión de que lo llenes y aceptes los términos y condiciones de Spotify.

 ![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/33b71432-bb5d-4ac9-a788-843eccdf1a98)

 Una vez que tengas tu app creada, ingresa en ella dando clic en el nombre y te aparecerá la siguiente pantalla:

 ![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/daa53090-df0a-4ac6-8911-7cba0efcd50b)

 Ahora debemos dar clic en settiings.

 ![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/27238794-fc7e-4daa-8027-fffde11f9d8b)

Lo importante aquí es el client id y el client secret, ya que los vamos a necesitar por que las vamos a usar como credenciales para poder generar el token que nos va a permitir conectarlos a los datos de Spotify.

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/8e1dedca-7bec-44ec-b6e3-a39a6e20d349)

Te recomiendo que guardes estos 2 datos en un bloc de notas.

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/3cbfc217-8740-4771-a53f-c35443d88b7b)

ahora vámonos hasta el footer de la página y vamos a dar clic en WEB API, aqui es donde estará la documentación.

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/6b8a4354-2519-4099-9f8a-6835e3b4da11)
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/c1cc0e44-bce2-4ef7-b472-5b6794d2bd77)

en la sección de REFERENCES puedes ver todos los datos que puedes consumir:

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/b812e4e9-48eb-461a-98a7-d3c5ed8926d2)
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/3c567db5-aa01-4c53-acd4-b63817b26f76)

Además que el sitio web te da ejemplos de los endpoints para que pruebes y también te dice con que estructura te va a llegar la información.

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/27850f36-ae6b-407a-ad20-49ff8fc23dff)
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/16c7b83d-1db8-4b9d-b4d3-be0c58efefcb)

GENERANDO EL TOKEN DESDE POSTMAN
Muy bien, ahora usaremos la herramienta de postman, que nos permite realizar diferentes peticiones a apis, la usaremos para generar el token que nos va a permitir consumir los datos de la api.
Creamos una nueva petición tipo POST y en la sección de body le vamos a enviar los siguientes parámetros:
1.	grant_type: aquí pondremos: "client_credentials"
2.	client_id : aquí ponemos el client_id que tienes en tu bloc de notas
3.	client_secret: aquí ponemos el client_secret que tienes en tu bloc de notas
En la url ponemos: "https://accounts.spotify.com/api/token" y finalmente damos clic en send para realizar la petición, si todo salió correcto en la parte inferior tendremos como resultado un objeto donde buscaremos la propiedad acces_token, este es el token que usaremos en nuestra app de angular, hay que tomar en cuenta que solo dura 1 hora.

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/5b85ab91-00a0-4244-ad27-53c3bed2fa30)

CONSUMIENDO DATOS DESDE POSTMAN
Ahora, vamos a crear la siguiente petición para probar que nuestro token sirve:
•	url: https://api.spotify.com/v1/artists/[tu id]/albums
•	headers: Authorization: Bearer BQBlZlrlcegVN_ZaeVjfjrBGq1BvYgXG1e6ye1iSrci9KkTV7E6nkkUXeN8_AtlcNZO-turyYsuj5xYG9OPq8EO1gcQJbfBnQtrGZM4C5Vy1t1RuIUc

ojo, que te recomiendo que vayas a la documentación y desde ahí cheques los endpoints que te proporciona la misma pagina, ya que agarra el id de tu cuenta y en los headers que enviamos checamos que sea [Bear (token)], la palabra Bear, seguida de un espacio y después ponemos el token que hemos generado.
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/16829e34-0abc-4907-932f-9e3991d60817)

Sí todo ha salido bien en el body tendremos como resultado un objeto con toda la información, genial, ¡ya hemos consumido la api de spotify!
CONSUMIENDO LA API DESDE IONIC CON ANGULAR
Omitiré los pasos para crear la aplicación, yo estoy usando la ultima versión de ionic y de angular (v16), además que estoy usando componentes standalone, esta es la estructura de la app ( la puedes clonar del repositorio de github):
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/783f307b-67e3-462c-9787-66086a9aac64)
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/add52842-35c3-4676-8dd8-ad2dbea59cea)

Es importante aclarar que en el app.component estoy importando el HttpClientModule y ademas el servicio que usaremos (SpotifyService) lo estoy poniendo como proveedor:

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/11109699-6ae6-4921-868b-2aec6daae61f)

En el Spotify Service he creado la variable TOKEN, que es donde pondremos el token generado desde postman.

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/897c3596-e0e9-446e-a768-f90fe4e6a56c)

Ahora analizando la función para ir por los artistas y albums.
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/433007b1-39cd-4291-8c10-72cb3380253d)


creamos los headers, solamente es un objeto con la misma estructura que hemos puesto en postman, después usamos el servicio http ( que previamente hemos inyectado en el constructor) y hacemos la petición GET, ya después nos suscribimos y hacemos un par de cosillas para mapear la información a como la necesito para mostrarla en el componente HOME.
en el componente donde lo queremos usar, yo me cree la estructura de datos que están viendo, lo que me importa es remplazar la información estática del arreglo de "songs", entonces en el OnInit vamos a consumir el servicio y a asignarle el valor nuevo a ese arreglo.
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/bfdc8e89-c0e8-4dbd-8233-7396caff9b9f)
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/ce501fbe-3728-4310-b4f3-f26ee4031ae3)

como vez, solo le asigno los valores directamente, ahora veamos el HTML:
![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/f23a26e8-91c8-4a14-99f3-1836e900d842)

si te preguntas como cargo la información, tengo un componente albums en donde por medio de un input de entrada le paso cada uno de los objetos que esta iterando el NgFor:

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/8dfdb0f2-b541-482a-9afb-c1eb244bc67b)

ahí puedes ver como se le asignan las variables y pues por ultimo en el html tenemos lo siguiente:

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/ed58e98e-8acf-45a2-b4ca-3ea546fd1292)

y por último el resultado final es el siguiente:

![image](https://github.com/Johanserna1023/API-Apotify/assets/93808275/ae7f411a-671a-4a09-aaf4-96782031911e)

CONCLUSIONES

En resumen, saber cómo consumir APIs te permite acceder a servicios externos, ampliar las funcionalidades de tu aplicación, reutilizar recursos existentes y simplificar el mantenimiento a largo plazo. Esto te convierte en un desarrollador web más versátil y te ayuda a ofrecer una experiencia más completa y rica a tus usuarios.
Link del repositorio: https://github.com/Johanserna1023/API-Apotify














































