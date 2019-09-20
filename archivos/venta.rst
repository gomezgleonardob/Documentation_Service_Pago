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
.. csv-table:: **Configuración**
   :header: "Atributo", "Detalle"
   :widths: 40, 500

    "Seguridad", "La clave del del esb debe ser la inicial del resto del modulo admin.nombremodulo."
    "Persistencia", "Para la conexión a la base de datos debe esta compuesto de la siguiente manera : EngiMysql.NombredelProyecto.NombredelModulo"
    "Parametros", "Para la conexión a la base de datos debe esta compuesto de la siguiente manera : EngiParametros.NombredelProyecto.NombredelModulo"
    "Email","Se configura las variables de Asunto y Cuerpo para el envío de emails "
..

PERSISTENCIA
~~~~~~~~~~~~
Nombre del Archivo: EngiMysql.Maletero.Ventas.properties" ,este archivo debe ser agregado en la carpeta configuraciones del servidor Wildfly. 

.. csv-table:: **Persistencia de Datos**
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

.. csv-table:: **Parámetro**
   :header: "Atributo", "Detalle"
   :widths:100, 500

    "Nombre del parámetro ", "Valor que se le va asignar"
..

EMAIL
~~~~~
Nombre del Archivo: Engimail.properties" ,este archivo se especifican las variables del asunto y el cuerpo del email.

.. csv-table:: **Parámetros Email**
   :header: "Atributo", "Detalle"
   :widths: 100, 500

    "Nombre del asunto ", "Valor que se le va asignar"
    "Nombre del cuerpo html ", "Valor que se le va asignar"
..

PARÁMETROS DEL MICROSERVICIO
----------------------------

.. csv-table:: 
   :header: "Campo", "Detalle"
   :widths: 40, 500

    "Protocolo", "Para pruebas se usa http y para producción https."
    "IpServidor", "Ip o Url de producción solicitar a la persona encargada del modulo ESB."
    "ClaveAcceso", "Clave única de acceso."
    "Aplicacion","Tipo de plataforma desde donde se realiza la transacción ejemplo Chrome, Mozilla, Android, IOS."
    "IdAplicacion", "Id del dispositivo desde donde se realiza la transacción ejemplo: “browser-firefox|version-63.0.0|so-Windows10” desde un navegador web.."
    "Menu", "El menú hace referencia al microservicio que vamos a llamar y sobre la entidad que vamos a trabajar."
    "Abreviatura", "Iniciales de la tabla o entidad sobre las cuales se va a realizar la operación ejemplo si voy a listar persona la abreviatura es per."
    "Nombreclase","Nombre de la clase sobre la cual se va a realizar la operación por ejemplo GenericDao, este nombre debe estar especificado en la documentación del cada módulo."
    "Ip", "Ip del usuario que realiza la petición."
..

TRANSACCIONES
-------------

Las transacciones que se pueden realizar son las siguientes:

- Crear.
- Actualizar.
- Listar.
- Eliminar.

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

+-------------------+--------------------------------------------------------+-------------------+
|     Atributos     |         Campos                                         |     Requerido     |
+===================+========================================================+===================+
| pagid             |   Id del pago.                                         |         √         |
+-------------------+--------------------------------------------------------+-------------------+
| arcid             |    Objeto Archivo:                                     |         √         |
|                   |  - arcid: Id del archivo.                              |                   |
|                   |  - arcnombre: Nombre del archivo.                      |                   |
|                   |  - arcruta: Ruta donde se almacena el archivo.         |                   |
|                   |  - arcextension: Extensión del archivo.                |                   |
|                   |  - arcestado: Estado del archivo.                      |                   |
|                   |  - arceliminado: Eliminación del archivo.              |                   |
+-------------------+--------------------------------------------------------+-------------------+
| monid             |  Id de la moneda.                                      |           √       |
+-------------------+--------------------------------------------------------+-------------------+
| forid             |  Id de la forma de pago.                               |            √      |
+-------------------+--------------------------------------------------------+-------------------+
| solid             |  Id de la solicitud.                                   |         √         |
+-------------------+--------------------------------------------------------+-------------------+
| viaid             |  Id del viajero.                                       |         √         |
+-------------------+--------------------------------------------------------+-------------------+
| ofeid             |  Id de la oferta.                                      |         √         |
+-------------------+--------------------------------------------------------+-------------------+
| usuid             |  Id del usuario.                                       |          √        |
+-------------------+--------------------------------------------------------+-------------------+
| pagcomprobante    |  Nombre del comprobante de pago.                       |           √       |
+-------------------+--------------------------------------------------------+-------------------+
| pagfechacreacion  |  Fecha de creación del pago.                           |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagfechapago      |  Fecha de validación   del pago.                       |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagfechaenviado   |  Fecha de envío de la compra.                          |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagfechaentregado |  Fecha de recepción de la compra.                      |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagfechaentregado |  Fecha de recepción de la compra.                      |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagfechaenviado   |  Fecha de envío de la compra.                          |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagfechaenviado   |  Fecha de envío de la compra.                          |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagfechacancelado |  Fecha de cancelación del pago.                        |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagvalor          |  Valor del pago.                                       |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagtraida         |  Valor de la importación.                              |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagcomision       |  Valor de la comisión.                                 |                   |
+-------------------+--------------------------------------------------------+-------------------+
| pagestado         |  Estado del pago.                                      |                   |
+-------------------+--------------------------------------------------------+-------------------+
..

.. tip::

   Los campos de la entidad que son requeridos ``√``  son necesarios, no pueden llevar  valores ``null``.  


TRANSACCIONES
^^^^^^^^^^^^^

CREAR 
~~~~~

Esta transacción recibe la petición para crear un pago, cuando el pago es creado puede llevar uno de los siguientes estados.

**URL**



   http://localhost:8080/engideveloper.esb-1.0/microservicio/ejecutar?abreviatura=pag&menu=maletero_ventas.Pago&nombreclase=Pago&accion
   =crear&ip=200.55.237.21&claveacceso=b80eec776186087e832f4cb55b0f4ede&idtransaccion=1&aplicacion=chrome&idaplicacion=browser-chrome|
   version-75.0.3770|so-Linux



* 0: El pago va a ser creado ,esta pendiente de verificación.
* 1 : El pago va a ser creado  y es verificado.

**JSON IN**

.. code-block:: javascript

  {
      "detail": [
       {
         "objeto": {
           "pagid": "",
           "arcid": null,
           "forid": 12345,
           "monid": 1,
           "ofeid": "05706ef0823560c689dd64dd84b32814",
           "solid": "21232f297a57a5a743894a0",
           "usuid": "1",
           "viaid": "992ea990dafb4f59a926ed80be51491b",
           "pagvalor": 300,
           "pagestado": 1,
           "pagtraida": 100,
           "pagcomision": 0,
           "pagfechapago": null,
           "pagcomprobante": "Cheque Certificado",
           "pagfechaenviado": null,
           "pagfechacreacion": "2019-08-14 09:15:20.000000",
           "pagfechacancelado": null
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
       "percorreo": "jeisson.millos@hotmail.com",
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

Creación del pago con validación.

.. code-block:: javascript

     {
        "detail": [
            {
           "objeto": {
            "pagid": "",
            "arcid": {
               "arcid": "",
               "arcnombre": "",
               "arcruta": "engideveloper/desarrollo/archivos/Categoria/Logo/",
               "arcextension": "png",
               "archivob64": "iVBORw0KGgoA...."
              },
             "forid": 12345,
             "monid": 1,
             "ofeid": "05706ef0823560c689dd64dd84b32814",
             "solid": "21232f297a57a5a743894a0",
             "usuid": "1",
             "viaid": "992ea990dafb4f59a926ed80be51491b",
             "pagvalor": 300,
             "pagestado": 1,
             "pagtraida": 150,
             "pagcomision": 0,
             "pagfechapago": null,
             "pagcomprobante": "Cheque Certificado",
             "pagfechaenviado": null,
             "pagfechacreacion": "2019-08-14 09:15:20.000000",
             "pagfechacancelado": null
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
         "percorreo": "jeisson.millos@hotmail.com",
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


Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.

ACTUALIZAR 
~~~~~~~~~

Esta transacción recibe la petición  para actualizar un pago.


**ESTADOS DEL PAG0**

Esta transacción recibe la petición para crear un pago, cuando el pago es creado puede llevar uno de los siguientes estados.

.. csv-table:: 
   :header: "Atributo", "Detalle"
   :widths: 40, 200

    "O", "Pendiente de verificación."
    "1", "Verificado"
    "2", "Enviado"
    "3", "Receptado"
    "5", "Cancelado"
..

   
**JSON IN**

.. code-block:: javascript

  {

    "detail":[
        {
            "objeto":{
                "pagid":"f8968d3df4aa94f4b0d6c6624ae878c4",
                "forid":12345,
                "arcid":null,
                "monid":1,
                "ofeid":"05706ef0823560c689dd64dd84b32814",
                "solid":"21232f297a57a5a743894a0",
                "usuid":"1",
                "viaid":"992ea990dafb4f59a926ed80be51491b",
                "pagvalor":300,
                "pagtraida":100,
                "pagcomision":30,
                "pagfechapago":null,
                "pagcomprobante":"Transferencia",
                "pagfechaenviado":"2019-08-16",
                "pagfechaentregado":null,
                "pagfechacreacion":"2019-08-14 09:15:20.000000",
                "pagfechacancelado":null,
                "pagestado": 2
            }
        }
    ],
    "generarid":false,
    "usuario":{
        "usuid":"1",
        "usuclave":"21232f297a57a5a743894a0e4a801fc3",
        "usuverificado":1,
        "usucodigoverificacion":"SU91L9",
        "usufechacodigo":"2019-07-08 11:27:36",
        "usufechacreacion":"2019-07-08 11:27:36",
        "usuestado":"Activo",
        "usueliminado":"No",
        "perid":{
            "perid":"1",
            "peridentificacion":"1725101784",
            "pernombre":"admin",
            "perapellido":"",
            "pertelefono":"",
            "percorreo":"jeisson.millos@hotmail.com",
            "perfechanacimiento":"2017-05-23 00:00:00",
            "perestado":"Activo",
            "pereliminado":"No",
            "sexid":1
        },
        "lenid":"es"
    },
    "rol":{
        "rolid":1,
        "rolnombre":"Administrador",
        "roldescripcion":"Rol para administrador",
        "rolestado":"Activo",
        "roleliminado":"No",
        "palid":1
    }

 }

..

Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.

**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripción"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"


CANCELAR
~~~~~~~~
Está transacción  recibe la petición para cancelar un pago, tomar en cuenta cancelado el pago automáticamente se anula la oferta.

.. note::

   El pago cuando tiene estado ``Cancelado`` automáticamente se cancela la ``Oferta`` y  ``Solicitud`` relacionada al pago.
   El archivo del comprobante pasa a un estado  ``Inactivo``


.. code-block:: javascript

 {

    "detail":[
        {
            "objeto":{
                "pagid":"59e57062ef43bb171dbf199fa8cdb9ce",
                "arcid":{
                    "arcid":"79acdccf7e3cca359f83ae693cca1bfd",
                    "arcnombre":"",
                    "arcruta":"engideveloper/desarrollo/archivos/Categoria/Logo/",
                    "arcextension":"png" 
                    "arcestado:"Inactivo" 
                    "arceliminado:"No" 
                },
                "forid":12345,
                "monid":1,
                "ofeid":"05706ef0823560c689dd64dd84b32814",
                "solid":"21232f297a57a5a743894a0",
                "usuid":"1",
                "viaid":"992ea990dafb4f59a926ed80be51491b",
                "pagvalor":300,
                "pagestado":5,
                "pagtraida":100,
                "pagcomision":30,
                "pagfechapago":"2018-08-27",
                "pagcomprobante":"Cheque Certificado",
                "pagfechaenviado":"2019-08-30",
                "pagfechacreacion":"2019-08-14 09:15:20.000000",
                "pagfechacancelado":"2019-08-30"
            }
        }
    ],
    "generarid":false,
    "usuario":{
        "usuid":"1",
        "usuclave":"21232f297a57a5a743894a0e4a801fc3",
        "usuverificado":1,
        "usucodigoverificacion":"SU91L9",
        "usufechacodigo":"2019-07-08 11:27:36",
        "usufechacreacion":"2019-07-08 11:27:36",
        "usuestado":"Activo",
        "usueliminado":"No",
        "perid":{
            "perid":"1",
            "peridentificacion":"1725101784",
            "pernombre":"admin",
            "perapellido":"",
            "pertelefono":"",
            "percorreo":"jeisson.millos@hotmail.com",
            "perfechanacimiento":"2017-05-23 00:00:00",
            "perestado":"Activo",
            "pereliminado":"No",
            "sexid":1
        },
        "lenid":"es"
    },
    "rol":{
        "rolid":1,
        "rolnombre":"Administrador",
        "roldescripcion":"Rol para administrador",
        "rolestado":"Activo",
        "roleliminado":"No",
        "palid":1
    }
 }



LISTAR
~~~~~~

Está transacción  recibe la petición para listar un pago, los filtros pueden ser los siguientes.

**FILTROS**

.. csv-table:: 
   :header: "Campo", "Descripción"
   :widths: 40, 100

    "pagid", "Id del Pago"
    "pagestado", "Estado del Pago"
    "pagid", "Id del Pago"
    "pagestado", "Estado del Pago"
    "forid","Id de la Forma de Pago"
    "viaid","Id del Viajero"
    "solid","Id  de la Solicitud"
    "usuid","Id del Usuario"
    "monid","Id de la Moneda"
    "pagcomprobante","Nombre del Comprobante"
    "pagfechacreacion","Fecha de Creación del Pago"
    "pagfechapago","Fecha de Creación del Pago"
    "pagfechaenviado","Fecha de Envío"
    "pagfechaentregado","Fecha de Envío"
    "pagfechacancelado","Fecha de Cancelación del Pago"
    "pagestado","Estado del Pago"
..


**JSON IN**

.. code-block:: javascript

       {
       "limit": "10",
       "orderby": "",
       "filtro": {
        "pagid": "",
        "pagestado": "Activo"
       },
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
        "percorreo": "jeisson.millos@hotmail.com",
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


**JSON OUT**

.. code-block:: javascript

  [
    {    
       "pagid":"f8968d3df4aa94f4b0d6c6624ae878c4",
       "forid":12345,
       "arcid":null,
       "monid":1,
       "ofeid":"05706ef0823560c689dd64dd84b32814",
       "solid":"21232f297a57a5a743894a0",
       "usuid":"1",
       "viaid":"992ea990dafb4f59a926ed80be51491b",
       "pagvalor":300,
       "pagtraida":100,
       "pagcomision":30,
       "pagfechapago":null,
       "pagcomprobante":"Cheque Certificado",
       "pagfechaenviado":"2019-08-16",
       "pagfechaentregado":2019-08-18,
       "pagfechacreacion":"2019-08-14 09:15:20.000000",
       "pagfechacancelado":null,
       "pagestado": 3
    }
  ]

..

OFERTA
------

ENTIDAD
^^^^^^^

+-------------------+--------------------------------------------------------+-----------+
|     Atributos     |               Campos                                   |  Requerido|
+===================+========================================================+===========+
| ofertaPK          |  - ofeid: Id de la oferta generada por el sistema      |           |
|                   |  - solid: Id de la solicitud de compra.                |     √     |
|                   |  - viaid: Id del viajero que realiza la oferta.        |           |
+-------------------+--------------------------------------------------------+-----------+
| monid             |  Id de la moneda.                                      |     √     |
+-------------------+--------------------------------------------------------+-----------+
| ofefechaentrega   |  Fecha de entrega de la compra.                        |     √     |
+-------------------+--------------------------------------------------------+-----------+
| ofechacreacion    |  La fecha de creación es insertada por el sistema."    |     √     |
+-------------------+--------------------------------------------------------+-----------+
| ofevalor          |  Valor de la oferta.                                   |     √     |
+-------------------+--------------------------------------------------------+-----------+
| ofetraida         |  Valor de traída de la compra.                         |     √     |
+-------------------+--------------------------------------------------------+-----------+
| ofeestado         |  Estado del  oferta.                                   |     √     | 
+-------------------+--------------------------------------------------------+-----------+

.. note::

   La primary key ``OfertaPK`` esta compuesta  de tres campos:
   ``ofeid`` ,  ``solid``,  ``viaid``
   

TRANSACCIONES
^^^^^^^^^^^^^


CREAR 
~~~~~

Esta transacción recibe la petición para crear una oferta.

**URL DEL WEBSERVICE**

.. _Webservice: http://localhost:8080/engideveloper.esb-1.0/microservicio/ejecutar?abreviatura=ofe&menu=maletero_ventas.Oferta&nombreclase=Oferta&accion=crear&ip=200.55.237.21&claveacceso=b80eec776186087e832f4cb55b0f4ede&idtransaccion=1&aplicacion=chrome&idaplicacion=browser-chrome|version-75.0.3770|so-Linux

.. note::

   El tipo de datos que vamos a enviar al webservice son ``(mediatype/json)`` 

**JSON IN**


.. code-block:: javascript

   {
       "detail": [
     {
       "objeto": {
         "ofertaPK": {
           "ofeid": "",
           "viaid": "8577325c12d271c28ca1d58e31ae0578",
           "solid": "beab5726a4f3d29de293a210d4434495"
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
       "percorreo": "jeisson.millos@hotmail.com",
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

**URL DEL WEBSERVICE**

.. waring::

http://localhost:8080/engideveloper.esb-1.0/microservicio/ejecutar?abreviatura=ofe&menu=maletero_ventas.Oferta
&nombreclase=Oferta&accion=actualizar&ip=200.55.237.21&claveacceso=b80eec776186087e832f4cb55b0f4ede&idtransaccion=1
&aplicacion=chrome&idaplicacion=browser-chrome|version-75.0.3770|so-Linux

.. note::

   El tipo de datos que vamos a enviar al webservice son ``(mediatype/json)`` 


Esta transacción recibe la petición  para actualizar  una oferta , el atributo  que se puede actualizar es:

* Estado de la oferta.

**ESTADOS DE LA OFERTA**

Esta transacción recibe la petición para crear un pago, cuando el pago es creado puede llevar uno de los siguientes estados.

.. csv-table:: 
   :header: "Atributo", "Detalle"
   :widths: 40, 200

    "O", "Rechazada"
    "1", "Verificada"
    "2", "Cancelada"
    "3", "Aceptada"
..

- Actualización cuando la oferta es Rechazada.

.. code-block:: javascript

   {
       "detail": [
     {
       "objeto": {
         "ofertaPK": {
           "ofeid": "d27bb8672019709b96f0c9540c09dace",
           "viaid": "8577325c12d271c28ca1d58e31ae0578",
           "solid": "beab5726a4f3d29de293a210d4434495"
         },
         "ofevalor": 300,
         "ofetraida": 150,
         "ofefechanetrega": "2019-09-20",
         "ofefechacreacion": "2019-09-19 00:00:00.000000",
         "ofeestado": 0,
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
       "percorreo": "jeisson.millos@hotmail.com",
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


- Actualización cuando la oferta es Cancelada.

.. code-block:: javascript

   {
       "detail": [
     {
       "objeto": {
         "ofertaPK": {
           "ofeid": "d27bb8672019709b96f0c9540c09dace",
           "viaid": "8577325c12d271c28ca1d58e31ae0578",
           "solid": "beab5726a4f3d29de293a210d4434495"
         },
         "ofevalor": 300,
         "ofetraida": 150,
         "ofefechanetrega": "2019-09-20",
         "ofefechacreacion": "2019-09-19 00:00:00.000000",
         "ofeestado": 2,
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
       "percorreo": "jeisson.millos@hotmail.com",
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


- Actualización cuando la oferta es Aceptada

**JSON IN**

.. code-block:: javascript

   {
       "detail": [
     {
       "objeto": {
         "ofertaPK": {
           "ofeid": "d27bb8672019709b96f0c9540c09dace",
           "viaid": "8577325c12d271c28ca1d58e31ae0578",
           "solid": "beab5726a4f3d29de293a210d4434495"
         },
         "ofevalor": 300,
         "ofetraida": 150,
         "ofefechanetrega": "2019-09-20",
         "ofefechacreacion": "2019-09-19 00:00:00.000000",
         "ofeestado": 2,
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
       "percorreo": "jeisson.millos@hotmail.com",
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
   :header: "Código", "Descripción"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"

LISTAR
~~~~~~

**URL DEL WEBSERViCE**

.. tip::

http://localhost:8080/engideveloper.esb-1.0/microservicio/ejecutar??abreviatura=ofe&menu=maletero_ventas.VistaOferta&nombreclase=GenericDao&accion=listar&
ip=200.55.237.21&claveacceso=b80eec776186087e832f4cb55b0f4ede&idtransaccion=1&aplicacion=chrome&idaplicacion=browser-chrome|version-75.0.3770|so-Linux

..

Esta transacción recibe la petición filtrar una oferta.

**JSON IN**

.. code-block:: javascript

  {
    "limit": "200",
    "orderby": "ofefechacreacion",
    "filtro": {
      "ofeid": "16fc186ea750ab42510c2b578193cc74",
      "solid": "beab5726a4f3d29de293a210d4434495",
      "viaid": "96c83e72e24c60dcb815fa1072c85425",
      "monid": 1,
      "ofevalor": 300,
      "monnombre": "Dolar",
      "ofetraida": 150,
      "monsimbolo": "$",
      "monabreviatura": "USD",
      "ofestado": 1,
      "ofefechanetrega": "2019-09-20",
      "ofefechacreacion": "2019-09-19 00:00:00.000000",
      "viaidentificacion": "0104741806",
      "vianombrecomercial": "Alf"
     },
   "usuario": {
      "usuid": "1",
      " usuclave": "21232f297a57a5a743894a0e4a801fc3",
      "usuverificado": 1,
      "usucodigoverificacion": "SU91L9",
      "usufechacodigo": "2019-09-17 16:08:44",
      "usufechacreacion": "2019-09-17 16:08:44",
      "usuestado": "Activo",
      "usueliminado": "No",
    "perid": {
      "perid": "1",
      "peridentificacion": "1725101784",
      "pernombre": "admin",
      "perapellido": "",
      "pertelefono": ""
      "percorreo": "jeisson.millos@hotmail.com",
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


**FILTROS**

Se detalla por los campos que se puede filtrar la solicitud.

**FILTROS**

.. csv-table:: 
   :header: "Campo", "Descripción"
   :widths: 40, 100

    "ofeid", "Id de la oferta"
    "viaid","Id del Viajero"
    "solid","Id  de la Solicitud"
    "usuid","Id del Usuario"
     "ofevalor","Valor de la Oferta"
        "monnombre","Nombre de la Moneda"
    "ofetraida","Valor de la Importación"
        "monsimbolo","Simbolo de la Moneda"
        "monabreviatura":"Abreviatura de la Moneda"
        "ofestado","Estado de la Oferta"
        "ofefechanetrega","Fecha de Entrega"
        "ofefechacreacion","Fecha de Creación"
        "viaidentificacion","Identificacion del Viajero""
        "vianombrecomercial","Nombre del Viajero"
  

**JSON OUT**

.. code-block:: javascript

  [

    {
        "ofeid":"16fc186ea750ab42510c2b578193cc74",
        "solid":"beab5726a4f3d29de293a210d4434495",
        "viaid":"96c83e72e24c60dcb815fa1072c85425",
        "monid":1,
        "ofevalor":300,
        "monnombre":"Dolar",
        "ofetraida":150,
        "monsimbolo":"$",
        "monabreviatura":"USD",
        "ofestado":1,
        "ofefechanetrega":"2019-09-20",
        "ofefechacreacion":"2019-09-19 00:00:00.000000",
        "viaidentificacion":"0104741806",
        "vianombrecomercial":"Alf"
    },
    {
        "ofeid":"363b122c528f54df4a0446b6bab05515",
        "solid":"beab5726a4f3d29de293a210d4434495",
        "viaid":"96c83e72e24c60dcb815fa1072c85425",
        "monid":1,
        "ofevalor":300,
        "monnombre":"Dolar",
        "ofetraida":250,
        "monsimbolo":"$",
        "monabreviatura":"USD",
        "ofestado":1,
        "ofefechanetrega":"2019-09-22",
        "ofefechacreacion":"2019-09-19 00:00:00.000000",
        "viaidentificacion":"0104741806",
        "vianombrecomercial":"Alf"
    }
 ]

SOLICITUD
---------

ENTIDAD
^^^^^^^

Campos de la entidad Solicitud

.. csv-table::
   :header: "Campo", "Detalle"
   :widths: 40,200
   
    "solid", "Id de la solicitud "
    "usuid","Id de usuario"
    "catid","Id de la categoría"
    "dirid","Id  de la dirección"
    "arcid","Id del archivo"
    "monid","Id de la moneda"
    "arcid","Id de archivo del comprobante de pago"
    "solfechacreacion","Fecha de creación de la solicitud"
    "sollink","Link de la compra"
    "soldescripcion","Breve descripción de la compra"
    "solindicaciones","Fecha de recepción del producto"
    "solestado","Estado de la solicitud"  

..

TRANSACCIONES
^^^^^^^^^^^^^

CREAR
~~~~~

Se recibe una petición para crear una solicitud y puede llevar los siguientes elementos.

    • La solicitud lleva foto y el link.
    • La solicitud lleva imgaen.
    • La solicitud lleva el link.

.. note::

   Cuando se crea la solicitu la imagen adjunta debe ir codificada en ``Base64`` y solo se archivos ``PNG``.
   La codificación la puede realizar en el siguiente enlace: `Codifación Base 64 <https://base64.guru/converter/encode/image/png>`_

**JSON IN** 


Solicitud creada que lleva link e imagen. 

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
      "percorreo": "jeisson.millos@hotmail.com",
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


- Solicitud creada que lleva solo el link

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
      "percorreo": "jeisson.millos@hotmail.com",
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

- Solicitud creada que lleva solo la imagen.

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
         "sollink": "",
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
      "percorreo": "jeisson.millos@hotmail.com",
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
    "errorVentas001","Error: solo se permiten archivos .png, .jpg o jpeg"
    "errorVentas002","Error: Debe ingresar una foto o link para la solicitud"

ACTUALIZAR
~~~~~~~~~~

**JSON IN** 

.. code-block:: javascript

 {
    "detail":[
        {
            "objeto":{
                "solid":"10ea061a148e904e72f793926614e8e4",
                "usuid":"db97b24be40c3d68ebec588209e41b36",
                "catid":"9ca40f9be9423c169f395626f80e3c07",
                "dirid":"25296619b814452080f7ae451309b545",
                "arcid":{
                    "arcid":"",
                    "arcnombre":"",
                    "arcruta":"",
                    "arcextension":"",
                    "archivob64":""
                },
                "solfechacreacion":"2019-07-31 13:04:35",
                "sollink":"https://articulo.mercadolibre.com.ec/MEC-420895304-memoria-ram-ddr3-2gb4gb-8gb-laptoppc-mayor-detal-nuevas-_JM?quantity=1",
                "soldescripcion":"RAM",
                "solindicaciones":"Comprar la ddr3 1333",
                "solestado":1
            }
        }
    ],
    "generarid":true,
    "usuario":{
        "usuid":"1",
        "usuclave":"21232f297a57a5a743894a0e4a801fc3",
        "usuverificado":1,
        "usucodigoverificacion":"SU91L9",
        "usufechacodigo":"2019-07-08 11:27:36",
        "usufechacreacion":"2019-07-08 11:27:36",
        "usuestado":"Activo",
        "usueliminado":"No",
        "perid":{
            "perid":"1",
            "peridentificacion":"1725101784",
            "pernombre":"admin",
            "perapellido":"",
            "pertelefono":"",
            "percorreo":"jeisson.millos@hotmail.com",
            "perfechanacimiento":"2017-05-23 00:00:00",
            "perestado":"Activo",
            "pereliminado":"No",
            "sexid":1
        },
        "lenid":"es"
    },
    "rol":{
        "rolid":1,
        "rolnombre":"Administrador",
        "roldescripcion":"Rol para administrador",
        "rolestado":"Activo",
        "roleliminado":"No",
        "palid":1
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

LISTAR
~~~~~~

**FILTROS**

.. csv-table:: 
   :header: "Filtro", "Descripcion"
   :widths: 40, 100

    "solid", "Id de la solicitud "
    "usuid","Id de usuario"
    "catid","Id de la categoría"
    "dirid","Id  de la dirección"
    "monid","Id de la moneda"
    "solfechacreacion","Fecha de creación de la solicitud"
    "soldescripcion","Breve descripción de la compra"
    "solestado","Estado de la solicitud."  
..

.. note::

  El atributo catid  **Categoría** puede tener hasta un nivel 23,para filtrar podemos enviar los filtros en cascada para filtrar por distintos niveles de categoría.

**JSON IN**

.. code-block:: javascript

       {
       "limit": "10",
       "orderby": "",
       "filtro": {
        "solid": "",
        "solestado": "Activo"
       },
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
        "percorreo": "jeisson.millos@hotmail.com",
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


**JSON OUT**

.. code-block::  javascript

  [ 
    {    
         "solid":"75b7c126127c9499e26cfab14795a9b6",
         "usuid": "db97b24be40c3d68ebec588209e41b36",
         "catid": "9ca40f9be9423c169f395626f80e3c07",
         "dirid": "25296619b814452080f7ae451309b545",
         "arcid": {
            "arcid": "67p7c126127c9499e26cfab19705c8k7",
            "arcnombre": "",
            "arcruta": "engideveloper/desarrollo/archivos/Categoria/Logo/",
            "arcextension": "png",
            "archivob64": "W3j3QHli8OYN"
          },
         "sollink": "",
         "soldescripcion": "GPU",
         "solindicaciones": "Comprar la de 6GB"
      }
  ]

FORMA DE PAG0
-------------

ENTIDAD
^^^^^^^

Campos de la entidad Forma de Pago.


.. csv-table:: 
   :header: "Atributos", "Campos"
   :widths: 40, 100

    "forid", "Id de forma de pago."
    "palid", "Id de la palabra."
    "pal_palid", "Id de forma de pago"
    "forreferencia", "Nombre de la forma de pago"
    "fortipo", Tipo de pago"
    "formetodo", "Metodo de pago"
    "forestado", Estado de la forma de pago"
    "foreliminado", "Eliminacion de la forma de pago"

TRANSACCIONES
^^^^^^^^^^^^^

CREAR
~~~~~

Esta transacción recibe la petición para crear una forma de pago.

**JSON IN**

.. code-block:: javascript

   {
     "detail": [
       {
         "objeto": {
           "palid": 39,
           "pal_palid": 39,
           "forreferencia": "Deposito",
           "fortipo": 1,
           "formetodo": 1,
           "forestado": "Activo",
           "foreliminado": "no"
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
        "percorreo": "jeisson.millos@hotmail.com",
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

Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.

**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"

ACTUALIZAR
~~~~~~~~~~

Esta transacción recibe la petición para actualizar una forma de pago.

.. code-block:: javascript

   {
     "detail": [
       {
         "objeto": {
           "fordi":1,
           "palid": 39,
           "pal_palid": 39,
           "forreferencia": "Transferencia",
           "fortipo": 1,
           "formetodo": 1,
           "forestado": "Activo",
           "foreliminado": "no"
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
        "percorreo": "jeisson.millos@hotmail.com",
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

Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.

**JSON OUT**

.. csv-table:: 

   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"


LISTAR
~~~~~~

Esta transacción recibe la petición para listar una forma de pago.

**FILTROS**

.. csv-table:: 
   :header: "Filtro", "Descripción"
   :widths: 40, 100

    "forid", "Id de forma de pago."
    "forreferencia", "Nombre de la forma de pago"
    "fortipo", Tipo de pago"
    "formetodo", "Metodo de pago"
    "forestado", "Estado de la forma de pago"
    "foreliminado", "Eliminacion de la forma de pago"
..

.. code-block:: javascript

  {
       "limit": "10",
       "orderby": "",
       "filtro": {
        "forid": "",
        "forestado": "Activo"
       },
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
        "percorreo": "jeisson.millos@hotmail.com",
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

**JSON OUT**

.. code-block:: javascript

  [ 
    {
      "fordi":1,
      "palid": 39,
      "pal_palid": 39,
      "forreferencia": "Transferencia",
      "fortipo": 1,
      "formetodo": 1,
      "forestado": "Activo",
      "foreliminado": "no"
    }
  ]