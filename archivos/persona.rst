.. index::
   single: persona


MICROSERVICIO PERSONA
=====================

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
.. csv-table:: **Configuración**
   :header: "Atributo", "Detalle"
   :widths: 40, 500

    "Seguridad", "La clave del del esb debe ser la inicial del resto del modulo admin.nombremodulo."
    "Persistencia", "Para la conexión a la base de datos debe esta compuesto de la siguiente manera : EngiMysql.NombredelProyecto.NombredelModulo"
    "Parametros", "Para la conexión a la base de datos debe esta compuesto de la siguiente manera : EngiParametros.NombredelProyecto.NombredelModulo"
..


PERSISTENCIA
~~~~~~~~~~~~
Nombre del Archivo: EngiMysql.Maletero.Persona.properties" ,este archivo debe ser agregado en la carpeta configuraciones del servidor Wildfly. 

.. csv-table:: **Persistencia de Datos**
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
- Eliminar.


ENTIDADES
---------

Dentro del modulo persona tenemos las siguientes entidades.

- DIRECCION
- VIAJERO

DIRECCION
---------

**ENTIDAD**

.. csv-table:: 
   :header: "Atributo", "Detalle"
   :widths: 40, 100
 
    "dirid","Id de la direccion"
    "ciuid", "Id de la ciduad."
    "estid", "Id del estado."
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

**URL**


Esta transacción recibe la petición para crear una dirección.

.. code-block:: javascript

    {
      "detail": [
        {
          "objeto": {
            "dirid": "dir2",
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
   :header: "Código", "Descripción"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"

ACTUALIZAR
~~~~~~~~~~

Esta transacción recibe la petición para actualizar una dirección.

.. code-block:: javascript
  
       {
       "detail": [
          {
          "objeto": {
             "dirid": "dir2",
             "ciuid": 98,
             "estid": 4,
             "paisid": "2",
             "usuid": "1",
             "dirdireccion": "Challuabamba",
             "dirlatitud": "-2.33333",
             "dirlongitud": "-79.7377",
             "dircodigopostal": "101105",
             "dirtelefono": "984998988",
             "direstado": "Activo",
             "direliminado": "No"
            }
          }
        ],
      "generarid": false,
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

Esta transacción recibe la petición para listar una dirección, aquí se puede aplicar filtros que son los siguientes:

**FILTROS**

.. csv-table:: 
   :header: "Atributo", "Detalle"
   :widths: 40, 100
 
    "dirid","Id de la direccion"
    "ciuid", "Id de la ciduad."
    "estid", "Id del estado."
    "paisid", "Id del país"
    "usuid", "Id del usuario"
    "dirdireccion","Dirección"
    "dircodigopostal","Código postal"
    "dirtelefono","Número de teléfono"
    "direstado","Estado de la dirección"
..

**JSON IN**

.. code-block:: javascript

  {
    "limit":"10",
      "orderby":"",
         "filtro":{
           "usuid":"",
           "dirdireccion":"",
           "dircodigopostal":"",
           "direstado":"Activo"
         }
    }
    ,
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

.. code-block:: javascript

  [
    {
        "dirid": "100b8c126127c9499e26cfab14795at4erl",
        "ciuid": 4,
        "estid": 3,
        "paisid": "2",
        "dirdireccion": "Max Uhle y Roma",
        "dirlatitud": "-2.976543",
        "dirlongitud": "-79.90876",
        "dircodigopostal": "0113934",
        "dirtelefono": "593984997840",
        "direstado": "Activo",
        "direliminado": "No"
    },
    {
        "dirid": "67p7c126127c9499e26cfab19705c8k7",
        "ciuid": 4,
        "estid": 3,
        "paisid": "2",
        "dirdireccion": "Panamericana Norte KM 9.7",
        "dirlatitud": "-2.977666",
        "dirlongitud": "-78.123315",
        "dircodigopostal": "0103234",
        "dirtelefono": "593984997845",
        "direstado": "Activo",
        "direliminado": "No"
    },
    {
        "dirid": "75b7c126127c9499e26cfab14795a9b6",
        "ciuid": 4,
        "estid": 3,
        "paisid": "2",
        "dirdireccion": "Av Catolica y Las Americas",
        "dirlatitud": "-2.789012",
        "dirlongitud": "-80.01233",
        "dircodigopostal": "0102244",
        "dirtelefono": "593984998988",
        "direstado": "Activo",
        "direliminado": "No"
    },
    {
        "dirid": "775cc126127c9499e26cfab14795a9b9",
        "ciuid": 4,
        "estid": 3,
        "paisid": "2",
        "dirdireccion": "Calle Larga y 12 de abril",
        "dirlatitud": "-2.999678",
        "dirlongitud": "-77.3987",
        "dircodigopostal": "0101225",
        "dirtelefono": "593984997845",
        "direstado": "Activo",
        "direliminado": "No"
    },
    {
        "dirid": "98b7c126127c9499e26cfab14795a9b9",
        "ciuid": 4,
        "estid": 3,
        "paisid": "2",
        "dirdireccion": "Huayna Capac y Arrayan",
        "dirlatitud": "-2.987045",
        "dirlongitud": "-79.123315",
        "dircodigopostal": "0103234",
        "dirtelefono": "593984997845",
        "direstado": "Activo",
        "direliminado": "No"
    }
  ]

..

ELIMINAR LOGICAMENTE
~~~~~~~~~~~~~~~~~~~~

Esta transacción recibe la petición para eliminar una dirección.

.. note::

   Cuando se va eliminar la dirección el campo ``direliminado`` se le asigna un valor de ``si``.

**JSON IN**

.. code-block:: javascript

       {
       "detail": [
          {
          "objeto": {
             "dirid": "dir2",
             "ciuid": 98,
             "estid": 4,
             "paisid": "2",
             "usuid": "1",
             "dirdireccion": "Challuabamba",
             "dirlatitud": "-2.33333",
             "dirlongitud": "-79.7377",
             "dircodigopostal": "101105",
             "dirtelefono": "984998988",
             "direstado": "No",
             "direliminado": "Si"
            }
          }
        ],
      "generarid": false,
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


VIAJERO
-------

**ENTIDAD**

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
|                   |           - perapellido:Apellido de la persona         |
|                   |           - pertelefono:Teléfono                       | 
|                   |           - percorreo:Email                            | 
|                   |           - perfechadenacimiento:Fecha de Nacimiento   |
|                   |           - perestado:Estado                           |
|                   |           - pereliminado:Estado                        | 
|                   |                                                        | 
|                   |  - lenid: Id del lenguaje.                             |
|                   |  - usuclave: Clave del usuario.                        | 
|                   |  - usuverificado: Clave del usuario.                   | 
|                   |  - usucodigoverificacion: Código de verificación       | 
|                   |  - usufechacodigo: Fecha de envío del codigo.          | 
|                   |  - usufechacreacion: Fecha de creación del usuario.    | 
|                   |  - usufechaestado: Fecha de envío del codigo.          | 
|                   |  - usufechaeliminado: Fecha de envío del codigo.       | 
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

Al crear el viajero se pueden presentar dos casos:

 - El viajero puede estar asociado a un usuario.
 - El viajero es nuevo se crea  el usuario y la persona.


**JSON IN**

Viajero sin usuario.

.. code-block:: javascript

 {
  "detail": [
    {
      "objeto": {
        "viaidentificacion": "01047",
        "vianombrecomercial": "MotorSA",
        "viafechacreacion": null,
        "viaestado": null,
        "viaeliminado": null,
        "usuid": {
          "lenid": "es",
          "perid": {
            "perid": null,
            "sexid": 1,
            "peridentificacion": "01047",
            "pernombre": "Pedro",
            "perapellido": "Perez",
            "pertelefono": "010",
            "percorreo": "jeisson.millos@hotmail.com",
            "perfechanacimiento": "2002-12-20T05:00:00.000Z",
            "perestado": null,
            "pereliminado": null
          },
          "usueliminado": null,
          "usucodigoverificacion": null,
          "usufechacodigo": null,
          "usufechacreacion": null,
          "usugenerarclave": true
        },
        "arcid": {
          "arcextension": "png",
          "archivob64": "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"
        }
      }
    }
  ],
  "generarid": true,
  "usuario": {
    "usuid": "1",
    "usuclave": "21232f297a57a5a743894a0e4a801fc3",
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

- Viajero que tiene un usuario

.. code-block:: javascript

   {
       "detail": [
          {
       "objeto": {
         "usuid": {
            "usuid": "1",
            "perid": 1,
            "lenid": "es",
            "usuclave": "21232f297a57a5a743894a0e4a801fc3",
            "usuverificado": 1,
            "usucodigoverificacion": "SU91L9",
            "usufechacodigo": "2019-07-08 11:27:36",
            "usufechacreacion": "2019-07-08 11:27:36",
            "usuestado": "Activo",
            "usueliminado": "No"
            },
          "arcid": {
            "arcid": "",
            "arcnombre": "",
            "arcruta": "engideveloper/desarrollo/archivos/Categoria/Logo/",
            "arcextension": "png",
            "archivob64": "iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAQAAAAAYLlVAAAA
            BGdBTUEAALGPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA
            6mAAAF3CculE8AAAAAmJLR0QAAKqNIzI"
          },
          "vianombrecomercial": "Heinkel",
          "viaidentificacion": "0104741805"
           }
         }
       ],
       "usuario": {
         "usuid": "1",
         "usuclave": "21232f297a57a5a743894a0e4a801fc3",
         "usuverificado": 1,
         "usucodigoverificacion": "SU91L9",
         "usufechacodigo":  "2019-07-08 11:27:36",
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

.. note::

  - Cuando el ``Viajero`` se registra se le envía un correo con su código de verificación y se le asigna el rol ``viajero``.

**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"
    "errorPersona001","Error: la clave anterior no es la correcta"
    "errorPersona002","Error: la extension del archivo no es valida"
    "errorPersona003","Error: el usuario ya esta vinculado a un viajero"


ACTUALIZAR
~~~~~~~~~~

Esta transacción recibe la petición para actualizar un viajero.

**JSON IN**

.. code-block:: javascript

 {
   "detail": [
    {
      "objeto": {
        "viaid": "96c83e72e24c60dcb815fa1072c85425",
        "viaidentificacion": "0104741806",
        "vianombrecomercial": "Alf",
        "viafechacreacion": "2019-09-17 22:10:19",
        "viaestado": "Activo",
        "viaeliminado": "No",
        "usuid": {
          "usuid": "c77d26dfe297152ca5c43ad6f1435b9d",
          "usuclave": "d3a60ae8e326ade599952a372bb2f820",
          "usuclaverepetir": "d3a60ae8e326ade599952a372bb2f820",
          "lenid": "es",
          "perid": {
            "perid": "d97b0ce31fd8b81f247b389f6c7f6673",
            "sexid": 1,
            "peridentificacion": "0104741806",
            "pernombre": "Heinz",
            "perapellido": "Guderian",
            "pertelefono": "098111",
            "percorreo": "gomezgleonardob@protonmail.com",
            "perfechanacimiento": "1998-11-27T05:00:00.000Z",
            "perestado": "Activo",
            "pereliminado": "No"
          },
          "usuestado": "Activo",
          "usuverificado": 1,
          "usueliminado": "No",
          "usucodigoverificacion": "7337",
          "usufechacodigo": "2019-09-17 22:10:19",
          "usufechacreacion": "2019-09-17 22:10:19",
          "usugenerarclave": true
        },
        "arcid": {
          "arcid": "2e16e46d93186c97702885ad2732603b",
          "arcruta": "engideveloper/desarrollo/archivos/c77d26dfe297152ca5c43ad6f1435b9d/Viajero/Logo/",
          "arcextension": ".png",
          "arcestado": "Activo",
          "arceliminado": "No"
        }
      }
    }
  ],
  "generarid": true,
  "usuario": {
    "usuid": "1",
    "usuclave": "21232f297a57a5a743894a0e4a801fc3",
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
   :header: "Código", "Descripción"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"

LISTAR
~~~~~~
Esta transacción recibe la petición para listar un viajero.

**JSON IN**

.. code-block:: javascript



..

Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.

**JSON OUT**

.. code-block:: javascript

 [
  {
    "viaid": "96c83e72e24c60dcb815fa1072c85425",
    "viafechacreacion": "2019-09-17 22:10:19",
    "viaidentificacion": "0104741806",
    "vianombrecomercial": "Alf",
    "viaestado": "Activo",
    "viaeliminado": "No",
    "usuid": {
      "usuid": "c77d26dfe297152ca5c43ad6f1435b9d",
      "usuclave": "d3a60ae8e326ade599952a372bb2f820",
      "usuverificado": 1,
      "usucodigoverificacion": "7337",
      "usufechacodigo": "2019-09-17 22:10:19",
      "usufechacreacion": "2019-09-17 22:10:19",
      "usuestado": "Activo",
      "usueliminado": "No",
      "perid": {
        "perid": "d97b0ce31fd8b81f247b389f6c7f6673",
        "peridentificacion": "0104741806",
        "pernombre": "Heinz",
        "perapellido": "Guderian",
        "pertelefono": "098111",
        "percorreo": "gomezgleonardob@protonmail.com",
        "perfechanacimiento": "1998-11-27 00:00:00",
        "perestado": "Activo",
        "pereliminado": "No",
        "sexid": 1
      },
      "lenid": "es"
    },
    "arcid": {
      "arcid": "2e16e46d93186c97702885ad2732603b",
      "arcruta": "engideveloper/desarrollo/archivos/c77d26dfe297152ca5c43ad6f1435b9d/Viajero/Logo/",
      "arcextension": ".png",
      "arcestado": "Activo",
      "arceliminado": "No"
    }
  }
]

..
