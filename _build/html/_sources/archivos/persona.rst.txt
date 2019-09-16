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
- EliminarLogicamente.
- Listar.


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
                "usuid":{
            "perid":{
                "sexid":1,
                "peridentificacion":"0104741806",
                "pernombre":"Erwin",
                "perapellido":"Perez",
                "pertelefono":"072853044",
                "percorreo":"gomezgleonardob@protonmail.com",
                "perfechadenacimiento":"2019-05-03"
            },
            "lenid":"es",
            "usugenerarclave":true
        },
        "arcid":{
            "arcid":"",
            "arcnombre":"",
            "arcruta":"engideveloper/desarrollo/archivos/Categoria/Logo/",
            "arcextension":"png",
            "archivob64":"W3j3QHli8OYN"
        },
        "vianombrecomercial":"Heinkel",
        "viaidentificacion":"0104741805"
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
         "viaid": "6mAAAF3CculE9iu9klo"
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
          "viafechacreacion": "2019-08-10",
          "vianombrecomercial": "Arado Ar",
          "viaidentificacion": "0104741805",
          "viaestado": "Activo",
          "viaeliminado": "No",
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
   :header: "Código", "Descripción"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"

LISTAR
~~~~~~
Esta transacción recibe la petición para listar un viajero.

**JSON IN**

.. code-block:: javascript

       {
       "limit": "10",
       "orderby": "",
       "filtro": {
        "viaid": "",
        "viaestado": "Activo"
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

.. code-block:: javascript

 [ 
   {
    
     "viaid": "75b7c126127c9499e26cfab14795a9b6",
     "usuario": {
         "usuid": "1",
         "perid": {
          "perid": "1",  
          "sexid": 1,
          "peridentificacion": "1725101784",
          "pernombre": "admin",
          "perapellido": "",
          "pertelefono": "",
          "percorreo": "blgomez@engideveloper.com",
          "perfechanacimiento": "2017-05-23 00:00:00",
          "perestado": "Activo",
          "pereliminado": "No",
         }
      "usuclave": "21232f297a57a5a743894a0e4a801fc3",
        "usuverificado": 1,
        "usucodigoverificacion": "SU91L9",
        "usufechacodigo": "2019-07-08 11:27:36",
        "usufechacreacion": "2019-07-08 11:27:36",
        "usuestado": "Activo",
        "usueliminado": "No",
      }   
     "arcid": {
       "arcid": "67p7c126127c9499e26cfab19705c8k7",
       "arcnombre": "",
       "arcruta": "engideveloper/desarrollo/archivos/Categoria/Logo/",
       "arcextension": ".png",
       "arcestado": "Activo",
       "arceliminado": "No",
     },
    "viaestado": "Activo",
    "viaeliminado": "No",
    "viafechacreacion": "2019-07-15 00:00:00.000000",
    "vianombrecomercial": "MotorSA"
   }
 ]