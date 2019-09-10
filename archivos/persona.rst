.. index::
   single: persona


MICROSERVICIO PERSONA
=====================


MICROSERVICIO VENTA
===================

CONFIGURACIONES
---------------


MÓDULO
^^^^^^
- Especificar en el archivo "engiAcceso" la clave del módulo.
- Crear un archivo para la persistencia a la base de datos en este caso "EngiMysql.EngiMaletero.Persona"
- Agregar la persistencia de JBOSS para el modulo en  archivo standalone-full.xml

PROYECTO
^^^^^^^^
- Crear el nombre de la persistencia y agregar al archivo persistence.xml
- Agregar los paquetes que deseamos importar en el persistence.xml


VARIABLES DE CONFIGURACIÓN
^^^^^^^^^^^^^^^^^^^^^^^^^^
GENERALES
~~~~~~~~~
.. csv-table:: Configuración
   :header: "Atributo", "Detalle"
   :widths: 40, 500

    "Seguridad", "La clave del del esb debe ser la inicial del resto del modulo admin.nombremodulo."
    "Persistencia", "Para la conexión a la base de datos debe esta compuesto de la siguiente manera : EngiMysql.NombredelProyecto.NombredelModulo"
    "Parametros", "Para la conexión a la base de datos debe esta compuesto de la siguiente manera : EngiParametros.NombredelProyecto.NombredelModulo"
..


PERSISTENCIA
~~~~~~~~~~~~
Nombre del Archivo: EngiMysql.Maletero.Ventas.properties" ,este archivo debe ser agregado en la carpeta configuraciones del servidor Wildfly. 

.. csv-table:: Persistencia de Datos
   :header: "Atributo", "Detalle"
   :widths: 40, 500

    "persistence.nombre", "Nombre de la persistencia para la conexión a la base."
    "jdbc.url", "URL de la base de datos"
    "jdbc.user", "Usuario"
    "jdbc.password", "Clave"
    "jdbc.driver", "Nombre del driver para la conexión"

..


TRANSACCIONES
-------------

Las transacciones que se pueden realizar son las siguientes:

- Crear.
- Actualizar.
- Listar.
- EliminarLogicamente.
- Listar.


ENTIDADES
---------

Dentro del modulo persona tenemos las siguientes entidades.

- DIRECCION
- VIAJERO

DIRECCION
---------

ENTIDAD

.. csv-table:: 
   :header: "Atributo", "Detalle"
   :widths: 40, 100
 
    "dirid","Id de la direccion"
    "ciuid", "Se envía el valor del transporte a modificar."
    "estid", "Se envía la fecha de entrega a modificar."
    "paisid", "Id del país"
    "usuid", "Id del usuario"
    "dirdireccion","Dirección"
    "dirlatitud","Coordenada de latitud"
    "dirlatitud","Coordenada de longitud"
    "dircodigopostal","Código postal"
    "dirtelefono","Número de teléfono"
    "direstado","Estado de la dirección"

..

TRANSACCIONES
^^^^^^^^^^^^^

CREAR
~~~~~


**JSON IN**

.. code-block:: javascript

   {
       "detail": [
        {
          "objeto": {
            "ciuid": 99,
            "estid": 3,
            "paisid": "1",
            "usuid": "2",
            "dirdireccion": "Av de las Americas",
            "dirlatitud": "-2.78921",
            "dirlongitud": "-79.735758",
            "dircodigopostal": "010111",
            "dirtelefono": "98499568710",
            "direstado": "Activo",
            "direliminado": "No"
        }
           }     
        ],
     "usuario": {
         "usuid": "1",
         "usuclave": "21232f297a57a5a743894a0e4a801fc3",
         "usuverificado": 1,
         "usucodigoverificacion": "SU91L9",
         "usufechacodigo": "2019-07-08 11:27:36",
         "usufechacreacion": "2019-07-08 11:27:36",
         "usuestado": "Activo",
         "usueliminado": "No",
     "perid": {
       "perid": "1",
       "peridentificacion": "1725101784",
       "pernombre": "admin",
       "perapellido": "",
       "pertelefono": "",
       "percorreo": "blgomez@engideveloper.com",
       "perfechanacimiento": "2017-05-23 00:00:00",
       "perestado": "Activo",
       "pereliminado": "No",
       "sexid": 1
              },
      "lenid": "es"
       },
        "rol": {
       "rolid": 1,
       "rolnombre": "Administrador",
       "roldescripcion": "Rol para administrador",
       "rolestado": "Activo",
       "roleliminado": "No",
       "palid": 1
     }
   }
..



Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.



**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"



ACTUALIZAR
~~~~~~~~~~

**JSON IN**


.. code-block:: javascript



..



Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.



**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"


LISTAR
~~~~~~

**JSON IN**


.. code-block:: javascript



..



Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.



**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"

VIAJERO
-------





+-------------------+--------------------------------------------------------+
|     Atributos     |         Campos                                         |
+===================+========================================================+
| viad              |   Id del viajero.                                      |
+-------------------+--------------------------------------------------------+
| arcid             |    Objeto Archivo:                                     |
|                   |  - arcid: Id del archivo.                              | 
|                   |  - arcnombre: Nombre del archivo.                      |
|                   |  - arcruta: Ruta donde se almacena el archivo.         | 
|                   |  - arcextension: Extensión del archivo.                |
|                   |  - arcestado: Ruta donde se almacena el archivo.       | 
|                   |  - arcextension: Extensión del archivo.                |
+-------------------+--------------------------------------------------------+
| usuid             |    Objeto Usuario:                                     |
|                   |  - usuid: Id del usuario.                              | 
|                   |                                                        | 
|                   |  - perid: Objeto Persona:                              |
|                   |           - perid:Id de la Persona.                    |                    
|                   |           - sexid:Id del sexo.                         | 
|                   |           - peridentificacion:Identificacion           | 
|                   |           - pernombre:Nombre de la persona             | 
|                   |           - perapellido:Apellido de la Persona         |
|                   |           - pertelefono:Apellido de la Persona         | 
|                   |  - arcextension: Extensión del archivo.                |
|                   |  - arcestado: Ruta donde se almacena el archivo.       | 
|                   |  - arcextension: Extensión del archivo.                |
+-------------------+--------------------------------------------------------+
| monid             |  Id de la moneda.                                      |
+-------------------+--------------------------------------------------------+
| ofefechaentrega   |  Fecha de entrega de la compra.                        |
+-------------------+--------------------------------------------------------+
| ofechacreacion    |  La fecha de creación es insertada por el sistema."    |
+-------------------+--------------------------------------------------------+
| ofevalor          |  Valor de la oferta.                                   |
+-------------------+--------------------------------------------------------+
| ofetraida         |  Valor de traída de la compra.                         |
+-------------------+--------------------------------------------------------+
| ofeestado         |  Estado del  oferta.                                   |
+-------------------+--------------------------------------------------------+

TRANSACCIONES
^^^^^^^^^^^^^

CREAR
~~~~~


**JSON IN**


.. code-block:: javascript



..



Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.



**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"



ACTUALIZAR
~~~~~~~~~~

**JSON IN**


.. code-block:: javascript



..



Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.



**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"


LISTAR
~~~~~~

**JSON IN**


.. code-block:: javascript



..



Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.



**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"