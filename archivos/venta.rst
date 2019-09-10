.. index::
   single: venta

MICROSERVICIO VENTA
===================

CONFIGURACIONES
---------------


MÓDULO
^^^^^^
- Especificar en el archivo "engiAcceso" la clave del módulo.
- Crear un archivo para la persistencia a la base de datos en este caso "EngiMysql.EngiMaletero.Venta"
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

PARÁMETROS
~~~~~~~~~~
Nombre del Archivo: EngiParametros.Maletero.Ventas.properties" ,este archivo debe ser agregado en la carpeta configuraciones del servidor Wildfly.

.. csv-table:: Parametros
   :header: "Atributo", "Detalle"
   :widths: 40, 500

    "Nombre del parámetro ", "Valor que se le va asignar"
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

Dentro del modulo producto tenemos los siguientes entidades.
 
- **PAGO**
- **FORMA DE PAGO**
- **OFERTA**  
- **SOLICITUD** 

PAGO
----

ENTIDAD
^^^^^^^

.. csv-table:: Entidad
   :header: "Atributo", "Detalle"
   :widths: 40, 500

    "Detail", "Se envía un array de objetos sobre los cuales se vaya a realizar una operación."

..


TRANSACCIONES
^^^^^^^^^^^^^

CREAR 
~~~~~
Esta transacción recibe la petición para crear un pago, cuando el pago es creado puede llevar uno de los siguientes estados.

* 0: El pago va a ser creado ,esta pendiente de verificación.
* 1 : El pago va a ser creado  y es verificado.

**JSON IN**


.. code-block:: javascript



..

Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.

ACTUALIZAR 
~~~~~~~~~

Esta transacción recibe la petición  para actualizar  una oferta , luego se enruta hacia el microservicio correspondiente y responde en un objeto con formato JSON.

eL que se pueden actualizar son :

* Moneda.
* Valor de la oferta.
* Fecha de entrega.

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


**FILTROS**

.. csv-table:: 
   :header: "Campo", "Descripcion"
   :widths: 40, 100

    "pagid", "Id del Pago"
    "pagestadp", "Estado del Pago"

**JSON OUT**


OFERTA
------

ENTIDAD
^^^^^^^


.. csv-table:: Entidad
   :header: "Atributo", "Detalle"
   :widths: 40, 100
  
   
    "OfertaPk",""
    "Ofetraida", "Se envía el valor del transporte a modificar."
    "Ofefechaentrega", "Se envía la fecha de entrega a modificar."
    "Ofechacreacion", "La fecha de creación es insertada por el sistema."
    "Ofechaestado", "El estado de la oferta puede  por un valor numérico."

..

TRANSACCIONES
^^^^^^^^^^^^^

CREAR 
~~~~~

Esta transacción recibe la petición para crear una oferta.

**JSON IN**


.. code-block:: javascript

   {
       "detail": [
     {
       "objeto": {
         "ofertaPK": {
           "ofeid": "",
           "viaid": "8577325c12d271c28ca1d58e31ae0578",
           "solid": "sol2"
         },
         "ofevalor": 300,
         "ofetraida": 150,
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

Esta transacción recibe la petición  para actualizar  una oferta , los atributos que se pueden actualizar son:

* Moneda.
* Valor de la oferta.
* Fecha de entrega.

**JSON IN**

.. code-block:: javascript

   {
       "detail": [
     {
       "objeto": {
         "ofertaPK": {
           "ofeid": "d27bb8672019709b96f0c9540c09dace",
           "viaid": "8577325c12d271c28ca1d58e31ae0578",
           "solid": "sol2"
         },
         "ofevalor": 300,
         "ofetraida": 150,
         "ofefechaentrega": "2019-08-10",
         "ofeestado": 4,
         "ofefechacreacion": "2019-07-30"
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



**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"

LISTAR
~~~~~~

Esta transacción recibe la petición filtrar una oferta


**JSON IN**


.. code-block:: javascript

   {
         {

            "limit":"10",
            "orderby":"",
                     "filtro":{
                            "ofertaPK":{
                                        "ofeid":"",
                                        "viaid":"",
                                        "solid":""
                                        },
                             "ofeestado":"Activo"
       },
          "usuario":{
          "usuid":"1",
          "usuclave":"21232f297a57a5a743894a0e4a801fc3",
         "usuverificado":1,
       }
   }
 
..


**FILTROS**

Se detalla por los campos que se puede filtrar la solicitud.

.. csv-table:: 
   :header: "Campo", "Descripcion"
   :widths: 40, 1000

    "ofertaPK", "John", 40
    "ofeestado", "John,0

**JSON OUT**





SOLICITUD
---------

ENTIDAD
^^^^^^^

Campos de la entidad Solicitud


TRANSACCIONES
^^^^^^^^^^^^^

CREAR
~~~~~

Se recibe una petición para crear una solicitud y puede llevar los siguientes elementos

    • La solicitud lleva foto y el link.
    • La solicitud lleva imgaen.
    • La solicitud lleva el link.

**JSON IN** 


- Solicitud creada con link e imagen 

.. code-block:: javascript

  { 
     "detail": [
      {
         "objeto": {
         "usuid": "db97b24be40c3d68ebec588209e41b36",
         "catid": "9ca40f9be9423c169f395626f80e3c07",
         "dirid": "25296619b814452080f7ae451309b545",
          "arcid": {
          "arcid": "",
          "arcnombre": "",
          "arcruta": "engideveloper/desarrollo/archivos/Categoria/Logo/",
          "arcextension": "png",
          "archivob64": "W3j3QHli8OYN"
         },
          "sollink": "https://www.ebay.com/itm/NVIDIA-GeForce-GTX....",
          "soldescripcion": "GPU",
          "solindicaciones": "Comprar la de 6GB"
        }
       }
      ],
      "generarid": true,
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


**JSON IN** 


- Solicitud creada lleva solo la imagen

.. code-block:: javascript

  { 
     "detail": [
      {
         "objeto": {
         "usuid": "db97b24be40c3d68ebec588209e41b36",
         "catid": "9ca40f9be9423c169f395626f80e3c07",
         "dirid": "25296619b814452080f7ae451309b545",
         "sollink": "https://www.ebay.com/itm/NVIDIA-GeForce-GTX....",
         "soldescripcion": "GPU",
         "solindicaciones": "Comprar la de 6GB"
        }
       }
      ],
      "generarid": true,
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

.. code-block:: javascript



Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.

**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"

LISTAR
~~~~~~



**FILTROS**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "ofeid", "Id de la Oferta"
    "ofeestado", "Estado de la oferta"
