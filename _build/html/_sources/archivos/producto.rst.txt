.. index::
   single: venta


MICROSERVICIO PRODUCTO
======================

CREACIÓN  DEL MODULO
--------------------

**Modulo**

- Especificar en el archivo "engiAcceso" la clave del del esb debe ser la inicial del resto del modulo admin.nombremodulo.
- Crear un archivo para la persistencia a la base de datos en este caso "EngiMysql.EngiMaletero.Persona".
- Agregar la persistencia del modulo en  archivo standalone.

**Proyecto**

- Crear el nombre de la persistencia con el nombre que se .
- Agregar los paquetes que deseamos importar en el persistence.xml.


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

- INTERES
- CATEGORIA

INTERES
-------

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

CATEGORIA
---------

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
           "catreferencia": "Tecnologia",
           "catnivel": 0,
           "catpadre": null,
           "palid": 1,
           "arcid": {
             "arcextension": "png",
             "archivob64": "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"
            }
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

   {
       "limit": "10",
       "orderby": "",
       "filtro": {
       "catid": "",
       "catestado": "Activo"
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





Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.



**JSON OUT**

.. csv-table:: 
   :header: "Código", "Descripcion"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"