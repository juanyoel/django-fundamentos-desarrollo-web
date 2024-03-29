# django-fundamentos-desarrollo-web

## INSTALACION DEL PROYECTO Y CONCEPTOS FUNDAMENTALES
* Instalar el subsitema de linux en windows.
  - Activar características de windows.
  - Activar Linux subsistem.
* Fundamentos para el desarrollo web y modelos de BD.

![image](https://user-images.githubusercontent.com/84333525/140072113-fb5894c0-6160-4c81-803d-33bd67c92314.png)

## NOTA: Como este curso es de fundamentos está dividido en varias carpetas, yo estaré creando apps por cada una de ellas, pondré el nombre de la app por sección.

## Sección Users -- Introducción

### MODELOS
* Los modelos son lo más imortante en nuestro web app. Son las tablas en la BD. La definición de como vamos a trabajar con esos datos.
* Definir modelos:
  - Los modelos se definen con clases y heredan de la clase Model que se importa *from django.db import models*

  ![image](https://user-images.githubusercontent.com/84333525/140080323-e04f3bf1-5745-4c15-8ba0-9fc9edcb23e7.png)

### NOTA
* Recordar que cuando creamos una app nueva en el proyecto tenemos que registrarla en las Installs_app en el archivo *settings.py*

![image](https://user-images.githubusercontent.com/84333525/140080668-54118acd-b53b-4c35-9645-ec9555472e42.png)

* Cuando hacemos cualquier cambio en los modelos, debemos reflejar estos cambios en la BD, para ello tenemos que correr las migraciones
  - python manage.py makemigrations
  - python manage.py migrate

* Recordar que a los campos de caracteres siempre tenemos que ponerle la longitud, poner atención a como hacemos para que este campo muestre opciones en el siguiente ejemplo:

![image](https://user-images.githubusercontent.com/84333525/140084180-ec4ee1f1-ede7-4e2a-8874-687f6b9a6805.png)

* Por defecto cuando creamos los modelos y creamos las migraciones de estos modelos el id o pk django lo hace de forma automática siento este un enetero autoincremental, cuando necesitamos definir una pk manualmente lo realizamos de la siguiente manera:

![image](https://user-images.githubusercontent.com/84333525/140087107-0938a4dd-8bc4-4e23-871c-0b680b49c945.png)

* Cuando queremos que un campo no se repita y sea unico usmos la propiedad unique como en el siguiente ejemplo:

![image](https://user-images.githubusercontent.com/84333525/140087579-45a75d32-2aec-42c5-b707-22df978b7251.png)

* La declaración de los campos se pueden hacer verbosos, lo que entiendo en hacer un campo verboso es que brinda una ayuda al desarrollador para saber que está creando o llenando.

![image](https://user-images.githubusercontent.com/84333525/140088952-16bb0a42-b0a8-4b3c-a13f-7fa433489200.png)

* También se pueden definir Meta opciones para nuestros modelos, aquí se pone todo lo que no sea un campo y se define como en el siguiente ejemplo:

![image](https://user-images.githubusercontent.com/84333525/140091577-6e2a57d5-e0bd-433b-b7b4-2176797882cd.png)

Por ejemplo con estos meta datos estaría definiendo como ordenaría las páginas, le cambiaría el nombre a la tabla en la bd, y le daría una descripción para cuando fuera una o varias, como los ejemplos anteriores.

* Los modelos al ser definidos como clases nos permiten entonces definirles funciones que nos pueden permitir un sin número de posibilidades de funcionalidad, esta es una técnica útil para poder mantener la lógica en un solo sitio.

![image](https://user-images.githubusercontent.com/84333525/140092931-8b2e1a78-5d0c-47a7-8f50-a91c92f4b67e.png)

* Podemos en los modelos también definir propiedades que son muy útiles a la hora de buscar alguna información específica del modelo con el que se está trabajando, a continuación un ejemplo de propiedad:

![image](https://user-images.githubusercontent.com/84333525/140093488-af8b57b7-afea-47b0-9d67-c359bf72d31c.png)

* Otro método de mucha importancia es el __str__(self): con este le estamos diciendo a django de que manera representar nuestros objetos en cada de texto, muy útil cuando necesitamos trabajar con el panel de administración por ejemplo.

![image](https://user-images.githubusercontent.com/84333525/140094150-d6f5e146-503a-4430-8c2a-e37134d7f676.png)

## Sección Posts -- QuerySets

## MODELOS 
* Creamos los 3 modelos Blog, Author, Entry, para poder estudiar las relaciones entre ellos y los querysets o sea CRUD.
* Algo a tener encuenta y es bueno aprender es el shell de python, al caul podemos acceder de la siguiente manera *python manage.py shell* con este comando accedemos a la consola interctiva de python con la cual podemos probar cualquier acción realizada con objetos, CRUD.
 - Por ejemplo para crear y guardar un objeto de tipo Blog lo hacemos de la siguiente forma: *from posts.models import Blog* donde le estamos diciendo con que modelo vamos a estar trabajando.
 - Para crear un objeto de este tipo ejemplo:
 
   ![image](https://user-images.githubusercontent.com/84333525/140175928-3d9546ea-f1a5-41d4-8f69-0f663cf0a6b9.png)

* Curo time: 1h23m --> Ejemplo del trabajo y relaciones entre los modelos. No me funcionó por eso dejo el tiempo para poder estudiarlo en caso de ser necesario.

![image](https://user-images.githubusercontent.com/84333525/140177511-a7705201-6f5f-4d39-b6bc-9919e90cf344.png)

* Elementos a tener en cuenta de la imagen anterior:
  - Primero la creación de un objeto de cualquier tipo.
  - Segundo como definimos la relación con foreignkey y many to many (observar que en este último caso es con la función *add()*)

* Así creamos objetos:

![image](https://user-images.githubusercontent.com/84333525/140178573-dbe2cf41-f9de-4583-b0e7-6780151a874d.png)

- Metodos: *save(); add();* *nombreModelo.campoModelo.add()* --> este último cuando es many to many aunque creo se puede aplicar en más casos, *nombreModelo.objects.create()*
  este último de especial importancia para la creación de objestos del modelo correspondiente, cuando se realiza de esta manera no tenemos que guardar usando .save(), *nombreModelo.propiedadModelo.all()* genera un QuerySet con todos los objetos de ese tipo.

* Así obtenems objetos:
  - nombreModelo.objects.all()
  - nombreModelo.objects.filter(propiedadModelo='someText')

![image](https://user-images.githubusercontent.com/84333525/140179684-0e4d940e-5cc9-4a78-814b-34cd44c37a34.png)

  - nombreModelo.objects.first()
 
![image](https://user-images.githubusercontent.com/84333525/140180100-40a08196-5f37-4ede-aea1-28c8f1db3f29.png)

- Ejemplos para filtrar por fecha y por rating. Time: 1h29m

  - nombreModelo.objects.get(id) : cuando ya sabemos exactamente que estamos buscando

![image](https://user-images.githubusercontent.com/84333525/140180900-1c26d8bd-4724-48ac-96cd-9a3bc0d29e1b.png)

* Limitar el queryset:
- Esto se hace cuando tenemos un gran volumen de información para limitar la búsqueda, en el próximo ejemplo lo limitamos a los 10 primeros elementos:

![image](https://user-images.githubusercontent.com/84333525/140181160-911b044f-7c16-4274-adc6-989e256a3cd0.png)

* Look up:
  - Esto es cuando se hacen filtros o búsquedas, en ejemplos anteriores lo hemos visto con le lte, gte, en el próximo ejemplo estamos filtrando por un campo que contenga el contenido exacto de lo que estamos buscando.

![image](https://user-images.githubusercontent.com/84333525/140181535-73e2437c-f1f1-4ef1-ad40-56588060a3f8.png)

  Si no quisieramos que fuera case sensitive:
  
 ![image](https://user-images.githubusercontent.com/84333525/140181625-1604a64c-e25a-4c27-a096-14d8167767e3.png)
 
 - Como estos existen muchos otros filtros como contains, icontains, istartswith, iendswith, etc.

 ![image](https://user-images.githubusercontent.com/84333525/140182175-ceff4217-ce8d-4f81-ae7c-6b779272b863.png)
 
* Spam look up: Es el nombre que entiendo :):
  - Se refiere a cuando voy a realizar búsquedas en propiedades que tontienen referencias a otros modelos, como en la de los foreignKey o el de las relaciones many to many, en el que necesitamos hacer búsquedas en esos objetos a los que se hace referencia.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### DADA LA IMPORTANCIA DE APRENDER BIEN EL TRABAJO DE LOS QUERYSETS Y LAS RELACIONES ENTRE MODELOS, REPETIRE TODO NUEVAMENTE PARA TENER MAYOR DOMINIO

### CREACION DE OBJETOS
* Abrimos el shell de python
* Creamos un blog de la siguiente forma:

![image](https://user-images.githubusercontent.com/84333525/140184345-b02b32b5-9ba1-41b6-ae4b-314b3bcf3f2a.png)

* Recordamos que en este punto aún no hemos guardado el objeto en la BD para ello usamos el metodo .save()

![image](https://user-images.githubusercontent.com/84333525/140184596-f3288675-78bf-4dfe-b6be-7e4eebe48238.png)

* Para obtener todos los blogs que tengo guardados en la BD uso el metodo .all()

![image](https://user-images.githubusercontent.com/84333525/140184720-be7da16f-ebae-4845-8ef1-5e948709361f.png)

* Podemos editar una propiedad específica de la siguiente manera:

![image](https://user-images.githubusercontent.com/84333525/140184928-2caf3b0f-f9cb-4282-ba05-37cf04d5521f.png)

* Cuando vamos a trabajar con fechas necesitamos importar datetime:

![image](https://user-images.githubusercontent.com/84333525/140185216-e4ad7cf6-2ac3-450a-a43d-38aeb10e67d0.png)

* Para actualizar el blog en la entrada, solo creamos otro blog ejemplo blog2 y realizamos la siguiente llamada entry.blog=blog2
* Veremos ahora como le hacemos para agregar many to many fields, lo primero es que creamos un autor y lo guardamos.

![image](https://user-images.githubusercontent.com/84333525/140189900-fcecd999-0e80-48b4-9f32-2c961added97.png)

* Para agregar un nuevo autor lo hacemos de la siguiente manera recordar que lo hacemos así porque es many to many, o sea puede tener muchos auotres por lo que utilzamos el método add.

![image](https://user-images.githubusercontent.com/84333525/140190123-04fbcaa7-87e1-4ed1-947d-de4edda13556.png)

* Si necesitaramos adicionar varios autores es de la misma manera solo separaríamos por coma.
* Otra manera de crear objetos es usando el método create() como en el siguiente ejemplo

![image](https://user-images.githubusercontent.com/84333525/140190743-4fad0553-5589-49a0-bb8e-eb9b15963fa9.png)

### RETRIEVE OBJECTS
* Hacemos referencias a obtener objetos de la BD

![image](https://user-images.githubusercontent.com/84333525/140191174-3581d8af-1e32-44f3-a85f-906b7b237914.png)

* Filtramos objetos básico

![image](https://user-images.githubusercontent.com/84333525/140192430-3779725d-58c3-4c6a-8de7-aa93d8e58edf.png)

* Obtenemos el primer objeto de Entry

![image](https://user-images.githubusercontent.com/84333525/140192607-cc253bb3-4937-4f5d-a6b5-a6984f2652aa.png)

* Filtrar por fecha, observar que se ponen _ _ para separar el campo de busqueda del campo del modelo:

![image](https://user-images.githubusercontent.com/84333525/140192872-a0fbab33-f320-4b26-823d-7833e43d4c6e.png)

* Filtrar por rating (entero), en este caso es por mayor que (gte), pero puder ser equal to o lower than

![image](https://user-images.githubusercontent.com/84333525/140193429-51698b0d-d350-4ece-8a58-dde25d8995e1.png)

* Los filtros se pueden encadenar.

### BUSQUEDA ESPECIFICA
* Cunándo sabemos lo que estamos buscando en vez de usar un filtro podemos usar la función get:

![image](https://user-images.githubusercontent.com/84333525/140318598-9fdbd7fe-1527-42a5-8c59-5fb5e7f22501.png)

* Limitar Querset, esto se usa por ejemplo cuando hacemos un .all() retorna todos los objetos que tenemos guardados en la BD, lo cual pudiera ser un gran volumen de información por lo que podemos limitar haciendo un slicing de la siguiente forma

![image](https://user-images.githubusercontent.com/84333525/140318978-c78754df-caba-4c5a-9675-550b8a4adc60.png)

En el primer ejemplo solo quiero los 10 primeros elementos de la lista y en el segundo todos los que se encuentren en ese intervalo.

### Field lookup (Búsqueda por campo)
* El valor del campo debe ser igual a la búsqueda, ejemplos case sensitive y case no sensitive
  
  ![image](https://user-images.githubusercontent.com/84333525/140319752-8d99b5d0-803a-4a5e-8ff0-40f8c6213c73.png)

* El valor de la búsqueda puede estar contenido en el valor del campo

![image](https://user-images.githubusercontent.com/84333525/140320098-ac9d89f8-9a9e-4aaf-a367-c64b6357a4a4.png)

* Búsqueda en campos que hacen referencias a otros modelos:

![image](https://user-images.githubusercontent.com/84333525/140321858-4e99e4a8-e3e8-4c4e-bd9a-42e753222258.png)

 * Imprimir todos los modelos en un ciclo

![image](https://user-images.githubusercontent.com/84333525/140322710-d8d287d6-447b-470f-b117-435e8640d894.png)

* Para consultas más complejas importamos el objeto Q de los modelos como veremos en el siguiente ejemplo:

![image](https://user-images.githubusercontent.com/84333525/140323895-493f8f18-ea92-4bb5-8338-45a9192a22ec.png)

En este caso estoy filtrando por la fecha

* Encadenar búsquedas ejemplo:

![image](https://user-images.githubusercontent.com/84333525/140325282-75f3d992-93b5-477e-a277-7ede939e78ed.png)

En este caso le estoy diciendo que la fecha sea una de esas dos y además que cumpla con que el rating tiene que ser igual 7

* MANY TO MANY. En este tipo de relaciones utilizmos *set* para obtener todas las relaciones

![image](https://user-images.githubusercontent.com/84333525/140326290-2db4a3fd-e521-4c9c-b0ea-b302a33e0902.png)

* Otra forma de hacer lo anterior es adicionando al campo many to many el related_name

![image](https://user-images.githubusercontent.com/84333525/140327077-f6246999-ed02-499a-88e7-ac2ea7f5f398.png)

![image](https://user-images.githubusercontent.com/84333525/140327413-b19d6933-e671-49df-bd89-92e6a7206e77.png)


## Sección URLs
* Los urls son los que nos permiten acceder a la información, extremadamente importantes, es a través de los urls que vamos a llamar a las funciones y la lógica de la app.
* La configuración raíz de las urls se encuentra en el archivo settings.py en la variable **ROOT_URLCONF**
* Si queremos utilizar expresiones regulares en las urls tenemos que importar re_path del módulo de urls de django.
* Para incluir las urls definidas en las apps, importamos y usamos include.
* Un ejemplo de url es la siguiente:
  
  ![image](https://user-images.githubusercontent.com/84333525/140335723-9f67ba13-a84e-4b0e-abed-8a08c75430c7.png
  
 - Tener en cuenta que lo que se encuentra entre brackets es lo que django puede obtener para realizar las operaciones.
 - Señalo un ejemplo con slug porque es una manera más limpia de escribir un url.

  ![image](https://user-images.githubusercontent.com/84333525/140338001-34107b37-b653-42fe-ab79-314b5072c794.png)

* Ejemplo de url con expresiones regulares:

![image](https://user-images.githubusercontent.com/84333525/140340812-29c9b221-d272-48d1-8137-f57f520a3eb9.png)

* Ejemplo de función para redireccionar, en el método reverse el string que recibe como parámetros --> 'entries:entry-detail' la primera es el namespace utilizado en las urls del proyecto y la segunda palabra el name de la url en el archivo urls.py de la app.

![image](https://user-images.githubusercontent.com/84333525/140400964-20f77b84-6c98-4237-bbaa-d3fb2806e8b0.png)

* Notas: Recordar que en el archivo urls.py del proyecto es dónde ubicaremos los path principales de la app, dónde haciendo uso del include que debemos importar, podemos agregar las urls de las diferentes apps que vayamos creando. En el archivo urls.py de la app recordar que siemre debemos declarar la variable app_name = nombreApp, además en la lista urlpatterns agregaremos las diferentes urls de las vistas, que una url está definida en el siguiente formato primer parametro la prefijo de la url o sea /nombreUrl/, luego la vista o función a la que se está intentando acceder, y por último el name con el que la vamos a identificar ejemplo:

![image](https://user-images.githubusercontent.com/84333525/140403221-90a55333-5335-4b18-83b7-bb0379d22805.png)

## SECCION VISTAS
* Partimos del concepto que las vistas son en sí la lógica que se va a ejecutar en el servidor para llevar a cabo una acción determinada, en este caso de ejemplos básicos lo estamos definiendo como funciones, pero normalmente las definimos como clases en dependencia de lo que se quiera, y dividimos en conceptos más completos como los ViewSet y ApiViews.
* Nota: se pueden definir también handlers para los diferentes códigos de respuesta del servidor.

![image](https://user-images.githubusercontent.com/84333525/140405913-53dbf3c7-f13a-42ff-938c-834d5ee95e06.png)

![image](https://user-images.githubusercontent.com/84333525/140405951-99cbc49a-1056-444d-94fc-dfe36efa17a5.png)

Tener en cuenta que de forma obligatoria siempre se le debe pasar el parámetro request a las funciones con las que se estén trabajando en las vistas.

* Para servir una vista en Django, (aunque es lo que se usa) retornamos el método render que recibe 3 parámetros, el request, el archivo .html que se va a retornar y por último el contexto que es dónde se encuentra la info que se va a retornar al cliente.

![image](https://user-images.githubusercontent.com/84333525/140412798-decf1da7-f4b6-4a58-98d5-2acb33078c1e.png)

* REDIRECT: también podemos redireccionar directamente.

  ![image](https://user-images.githubusercontent.com/84333525/140513734-db4eca22-a7a6-4512-905e-6a6a4b1b179c.png)

* Estos son los métodos más importantes de shortcuts

![image](https://user-images.githubusercontent.com/84333525/140514883-c1478e32-6124-4911-bffa-a0f6089b4276.png)


### VISTAS BASADAS EN CLASES
* Ya tieniendo la idea bastante clara de como funcionan las vistas, pasamos a ver las vistas basadas en clases.
* Una vista basada en clases nos permite acceder a nuestros códigos a través de funciones
* Para crear una vista basada en clases básica primero hacemos las importaciones necesarias, creamos la clase, recordar que siepre que trabajamos con clases a los métodos que se creen dentro de la misma hay que pasarle self como parámetro, hay que poner a heredar la clase creada de la clase que hayamos importado.

![image](https://user-images.githubusercontent.com/84333525/140516026-fc9b3a4d-cd26-4306-b85e-336df8650e27.png)

![image](https://user-images.githubusercontent.com/84333525/140516051-0be8be27-49ac-4f01-b478-0df326cd4163.png)

### Vistas GENERICAS
* Las vistas genericas vienen con django para funciones específicas.
* ListView: renderiza una lista de objetos, basado en self.models

![image](https://user-images.githubusercontent.com/84333525/140516825-ae8117d5-91bb-4af4-8382-bcbcdb8bd3b5.png)

![image](https://user-images.githubusercontent.com/84333525/140519288-a39a022d-8f02-4284-85cf-86c651b9faef.png)

En el caso de las listas esperan un modelo en el ejemplo anterior le pasamos Entry que es uno de los modelos que tenemos de ejemplo, más adelante en el curso se estará profundizando en el trabajo condatos reales.

### PLANTILLAS
* Para este momento el trabajo con las plantillas no es de prioridad, pero si que quiero aprenderlo bien, por lo que dejo el tiempo del curso en el que se habla sobre el tema:
  2H:20M
* Filtros que se pueden emplear cuando se trabaja con plantillas, me parece interesante y a tener en cuenta si lo necesito en fututros proyectos.

![image](https://user-images.githubusercontent.com/84333525/140524036-0da99ad5-469d-4405-944f-aa04fd0bfb63.png)

### FORMULARIOS
* Los formularios caen en el mismo punto anterior, me parece interesante pero no es mi prioridad en estos momentos, dejo tiempo para en casa de ser necesario revisar el curso nuevamente 2H:29M
* Para crear formularios, creamos el archivo *forms.py* y definimos nuestros formularios como clases, recordar que es a partir de los modelos que ya tenemos definidos.

![image](https://user-images.githubusercontent.com/84333525/140525376-c29261da-cc5f-40da-8836-f619b390dca1.png)

En el caso del ejemplo anterior es para visualizar las dos formas en las que podemos definir los formularios, ambas hasta donde entiendo hacen exactamente lo mismo

* En las vitas para la primera forma podemos trabajar con los datos de la siguiente forma

![image](https://user-images.githubusercontent.com/84333525/140622093-9b094c95-5d27-4b62-80de-bca119369d2c.png)

* Para la segunda debemos trabajar en la vista de la siguiente manera

![image](https://user-images.githubusercontent.com/84333525/140622228-c97afed8-35ea-48bc-85d8-b02efb6f06ce.png)

En lo personal creo que mucho más práctico

### IMAGENES
* Para trabajar con imágenes debemos tener instalado el paquete Pillow
* Recordar que siempre que trabajamos con modelos se deben crear y correr las migraciones, por otra parte el campos de imagen es el siguiente:

![image](https://user-images.githubusercontent.com/84333525/140622318-10d93f11-4d8c-4a9a-b4b6-221309b00b40.png)

* Una buena práctica cuando ya habíamos trabajado con un tipo de modelos en la BD y le adicionamos un campo nuevo es en caso de que se pueda especificarle que puede ser null y estar vacío de la siguiente forma

![image](https://user-images.githubusercontent.com/84333525/140622360-c3b54017-64ca-4e68-befb-08c2546807ad.png)

* Mostrar imagnes
  - En el html vinculamos de la siguiente manera
    
    ![image](https://user-images.githubusercontent.com/84333525/140622669-357ab368-2942-437c-a3a4-5e03fc5213f6.png)

 - Creamos una carpeta static
 - En las urls del proyecto adicionamos los archivos staticos como muestro a continuación

![image](https://user-images.githubusercontent.com/84333525/140623009-06d18905-781f-43c6-9d67-3eb6749b0b23.png)

- En la configuración adicionamos las siguientes variables
  
  ![image](https://user-images.githubusercontent.com/84333525/140623046-2227cce7-6cc8-4406-a21d-20f7fdada738.png)

Se le debe agregar el siguiente código a la vista

  ![image](https://user-images.githubusercontent.com/84333525/140623060-753ae41d-660a-4c14-a5bf-cf5105be4068.png)

* Lo relacionado con las imágenes se encuentra en el siguiente ejemplo del curso 2H50M

## FORMULARIOS TRABAJADOS EN CLASS VIEWS
* Los ejemplo anteriores son utilizando funciones, a continuación utilizaremos clases

![image](https://user-images.githubusercontent.com/84333525/140627809-388580d1-ff41-4281-a7f4-41a2c2c6a78e.png)

* Para lo anterior hacemos la siguiente importación

![image](https://user-images.githubusercontent.com/84333525/140627814-d009c378-580b-4af5-9b80-cdf2b3e1ff99.png)

* Por último modificamos el archivo *urls.py*

![image](https://user-images.githubusercontent.com/84333525/140627839-fc154af9-fb79-443f-843a-47e6372b51b8.png)
