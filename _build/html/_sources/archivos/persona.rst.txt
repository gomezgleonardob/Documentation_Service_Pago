.. index::
   single: persona


MICROSERVICIO PERSONA
=====================


CREACIÓN  DEL MODULO
----------------------

**Modulo**

- Especificar en el archivo "engiAcceso" la clave del del esb debe ser la inicial del resto del modulo admin.nombremodulo
- Crear un archivo para la persistencia a la base de datos en este caso "EngiMysql.EngiMaletero.Persona"
- Agregar la persistencia del modulo en  archivo standalone.full

**Proyecto**

- Crear el nombre de la persistencia con el nombre que se 
- Agregar los paquetes que deseamos importar en el persistence.xml


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

.. csv-table:: Entidad
   :header: "Atributo", "Detalle"
   :widths: 40, 100
  
    "Detail", "Se envía un array de objetos sobre los cuales se vaya a realizar una operación."
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