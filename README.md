# django-fundamentos-desarrollo-web

## INSTALACION DEL PROYECTO Y CONCEPTOS FUNDAMENTALES
* Instalar el subsitema de linux en windows.
  - Activar características de windows.
  - Activar Linux subsistem.
* Fundamentos para el desarrollo web y modelos de BD.

![image](https://user-images.githubusercontent.com/84333525/140072113-fb5894c0-6160-4c81-803d-33bd67c92314.png)

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

