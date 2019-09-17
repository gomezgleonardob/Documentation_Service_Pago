.. index::
   single: venta


MICROSERVICIO PRODUCTO
======================

CONFIGURACIONES
---------------

MÓDULO
^^^^^^
- Especificar en el archivo "engiAcceso" la clave del módulo.
- Crear un archivo para la persistencia a la base de datos en este caso "EngiMysql.EngiMaletero.Producto"
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
Nombre del Archivo: EngiMysql.Maletero.Producto.properties" ,este archivo debe ser agregado en la carpeta configuraciones del servidor Wildfly. 

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
- Cancelar.

ENTIDADES
---------

Dentro del modulo persona tenemos las siguientes entidades.

- INTERES
- CATEGORIA


INTERES
-------

**ENTIDAD**

.. csv-table:: 
   :header: "Código", "Descripción"
   :widths: 40, 100

    "intid", "Id del interés."
    "viaid", "Id del viajero."
    "catid", "Id de la categoría."
    "viaid", "Id del viajero."
    "inestado", "Estado del interés."
    "ineliminado", "Eliminación del interés."

TRANSACCIONES
^^^^^^^^^^^^^

CREAR
~~~~~

Esta transacción recibe la petición para crear un interés.

**JSON IN**

.. code-block:: javascript

  {
     "detail": [
      {
        "objeto": {
          "intid": "",
          "viaid": "via1",
          "catid": "b12223334444"
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
   :header: "Código", "Descripción"
   :widths: 40, 100

    "sucess000", "Transacción Exitosa"
    "error008", "Datos Inválidos"
    "errorcategoria001","Error: solo se permiten archivos .png"

ACTUALIZAR
~~~~~~~~~~

Esta transacción recibe la petición para crear un interés.

Los campos que se pueden actualizar del interés son:

- Viajero.
- Categoría.
- Estado.

**JSON IN**

.. code-block:: javascript

   {
      "detail": [
       {
         "objeto": {
           "intid": "A59IFU8Q6cCAoIC1qu",
           "viaid": "via1",
           "catid": "3ODk00CpEpqTJsPZDKcQ5",
           "inestado": "Activo",
           "inteliminado": "No"
          }
       }
     ],
     "generarid": "false",
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
    "errorcategoria001","Error: solo se permiten archivos .png"


LISTAR
~~~~~~

Esta transacción recibe la petición para listar un interés,aquí se puede aplicar filtros que son los siguientes:

**FILTROS**

.. csv-table:: 
   :header: "Código", "Descripción"
   :widths: 40, 100

    "intid", "Id del interés."
    "viaid", "Id del viajero."
    "catid", "Id de la categoría."
    "viaid", "Id del viajero."
    "inestado", "Estado del interés."

**JSON IN**

.. code-block:: javascript

   {
      "limit": "10",
      "orderby": "",
      "filtro": {
        "intid": "",
        "inestado": "Activo"
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
     "catid": "21232f297a57a5a743894a",
     "intid": "d41894808ec78f3d028fc06b22f2a85f",
     "viaid": "75b7c126127c9499e26cfab14795a9b6",
     "intestado": "Activo",
     "ineliminado": "No"
   }
 ]

CATEGORIA
^^^^^^^^^

**MODELO**

+-------------------+--------------------------------------------------------+
|     Atributos     |         Campos                                         |
+===================+========================================================+
| catid             |   Id de la categoría.                                  |
+-------------------+--------------------------------------------------------+
| arcid             |    Objeto Archivo:                                     |
|                   |  - arcid: Id del archivo.                              | 
|                   |  - arcnombre: Nombre del archivo.                      |
|                   |  - arcruta: Ruta donde se almacena el archivo.         | 
|                   |  - arcextension: Extensión del archivo.                |
|                   |  - arcestado: Ruta donde se almacena el archivo.       | 
|                   |  - arceliminado: Eliminación del archivo.              |
+-------------------+--------------------------------------------------------+
| palid             |  Id de la palabra.                                     |
+-------------------+--------------------------------------------------------+
| catreferencia     |  Descripción de la categoría.                          |
+-------------------+--------------------------------------------------------+
| catnivel          |  Nivel de la categoría.                                |
+-------------------+--------------------------------------------------------+
| catpadre          |  Categoría Padre.                                      |
+-------------------+--------------------------------------------------------+
| catestado         |  Estado de la categoría.                               |
+-------------------+--------------------------------------------------------+
| cateliminado      |  Eliminación de la categoría                           |
+-------------------+--------------------------------------------------------+

TRANSACCIONES
^^^^^^^^^^^^^

CREAR
~~~~~

Esta transacción recibe la petición para crear una categoria.

**JSON IN**

.. code-block:: javascript

     {
       "detail": [
        {
          "objeto": {
             "catid": "",
             "catreferencia": "Tecnologia",
             "catnivel": 0,
             "catpadre": "null",
             "palid":1,
             "arcid": {
               "arcid": "",
               "arcruta": "/archivos/Categoria/Logo/",
               "arcextension": "png",
               "archivob64": "iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAQAAAAAYLlVA
                AAABGdBTUEAALGPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAA
                AOpgAAA6mAAAF3CculE8AAAAAmJLR0QAAKqNIzIAAAAJcEhZcwAADsQAAA7E
                AZUrDhsAAAAHdElNRQfjCQsOKDIZAfTcAAAB2ElEQVRo3u2ZQStEURTHf40p
                hLGQmlCzUNTY2EhJKCkLK6YkDclCVhYWs2Mr2RtlbGTHF5BENj6AjSYLSVnM
                giw0k4zFzDQJ993zuuOk3nmr9+7/nPt753/ffa8eVGOR4h8di9VJQyiHOkD4
                h2u3PAEwSAOQ59rZbFF6TcOVNbBUPr+jSJEHh7e7FKyB7xH2lTVFn4Vqj+fa
                AITYpctC90Lappg8xq2mh6Td3cjDqjAwZH7oSiG3oJlpAF5J8PGLZppVAObZ
                cA8wQxMAJ5z+qsmyQghYYJOiuZzcgooBhwbNPVcAxBj2KicF6GQMgEcujboK
                nud6kVqQpK4M8m6ln2WNN5cdSAj1ESbMAilARKiHVvOwv604X15kpuggblPK
                H0DOq7HAMvs2pdTfhuoA/ixoIeWpGaglQIQtVx1Qt0AdwO9jOOepmWS9dgB5
                zjw1MbtS6haoA0gt6LFWZsj8iw6oA0gt6KdRmJEl5xLgmG5hxoLx81XfAnUA
                qQVp2oQZN24Bdlx3QN0CdQCpBQd0CDO2OXcJMCLeB47Mw+oWqANILYiLkQtu
                AQpCvWeoWxAABAABQAAQAAQAP70NU+X/eqWPr3YunM0WtQPo/fKrpZ7RWnZA
                3QJ1gE8Ja3VeRqLkhQAAACV0RVh0ZGF0ZTpjcmVhdGUAMjAxOS0wOS0xMVQx
                NDo0MDo1MCswMDowMIYQLAYAAAAldEVYdGRhdGU6bW9kaWZ5ADIwMTktMDkt
                MTFUMTQ6NDA6NTArMDA6MDD3TZS6AAAAGXRFWHRTb2Z0d2FyZQB3d3cuaW5r
                c2NhcGUub3Jnm+48GgAAAABJRU5ErkJggg=="
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

ACTUALIZAR
~~~~~~~~~~
Esta transacción recibe la petición para crear una categoria.

**JSON IN**

.. code-block:: javascript

    {
      "detail": [
         {
           "objeto": {
              "catid": "d41894808ec78f3d028fc06b22f2a85f",
              "catreferencia": "Tecnologia",
              "catnivel": 0,
              "catpadre": "null",
              "catestado": "Activo",
              "cateliminado": "No",
              "arcid": {
                "arcid": "2acdcb0e49419ff0509a10ad909eda24",
                "arcruta": "/archivos/Categoria/Logo/",
                "arcextension": "png",
                "arcestado": "Activo",
                "arceliminado": "No",
                "archivob64": "iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAQAAAAAYLlVAAAABGdBTUEAAL
                 GPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA6mAAAF3CculE8AAAAAm
                 JLR0QAAKqNIzIAAAAJcEhZcwAADsQAAA7EAZUrDhsAAAAHdElNRQfjCQsOKDIZAfTcAAAB2E
                 lEQVRo3u2ZQStEURTHf40phLGQmlCzUNTY2EhJKCkLK6YkDclCVhYWs2Mr2RtlbGTHF5BENj
                 6AjSYLSVnMgiw0k4zFzDQJ993zuuOk3nmr9+7/nPt753/ffa8eVGOR4h8di9VJQyiHOkD4h2
                 u3PAEwSAOQ59rZbFF6TcOVNbBUPr+jSJEHh7e7FKyB7xH2lTVFn4Vqj+faAITYpctC90Lapp
                 g8xq2mh6Td3cjDqjAwZH7oSiG3oJlpAF5J8PGLZppVAObZcA8wQxMAJ5z+qsmyQghYYJOiuZ
                 zcgooBhwbNPVcAxBj2KicF6GQMgEcujboKnud6kVqQpK4M8m6ln2WNN5cdSAj1ESbMAilARK
                 iHVvOwv604X15kpuggblPKH0DOq7HAMvs2pdTfhuoA/ixoIeWpGaglQIQtVx1Qt0AdwO9jOO
                 epmWS9dgB5zjw1MbtS6haoA0gt6LFWZsj8iw6oA0gt6KdRmJEl5xLgmG5hxoLx81XfAnUAqQ
                 Vp2oQZN24Bdlx3QN0CdQCpBQd0CDO2OXcJMCLeB47Mw+oWqANILYiLkQtuAQpCvWeoWxAABA
                 ABQAAQAAQAP70NU+X/eqWPr3YunM0WtQPo/fKrpZ7RWnZA3QJ1gE8Ja3VeRqLkhQAAACV0RV
                 h0ZGF0ZTpjcmVhdGUAMjAxOS0wOS0xMVQxNDo0MDo1MCswMDowMIYQLAYAAAAldEVYdGRhdG
                 U6bW9kaWZ5ADIwMTktMDktMTFUMTQ6NDA6NTArMDA6MDD3TZS6AAAAGXRFWHRTb2Z0d2FyZQ
                 B3d3cuaW5rc2NhcGUub3Jnm+48GgAAAABJRU5ErkJggg=="
                }
              }
            }
          ],
        "generarid": "false",
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
       "rolid":1,
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

LISTAR
~~~~~~

Esta transacción recibe la petición para listar un interés,aquí se puede aplicar filtros que son los siguientes:

**FILTROS**

.. csv-table:: 
   :header: "Código", "Descripción"
   :widths: 40, 100
   
    "catid", "Id de la categoría."  
    "catestado", "Estado del categoría."
    "catnivel", "Nivel de la categoría."
    "catpadre", "Categoría padre."

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

.. code-block:: javascript

  [
    {
     "catid": "21232f297a57a5a743894a",
     "arcid": {
       "arcid": "67p7c126127c9499e26cfab19705c8k7",
       "arcnombre": "",
       "arcruta": "engideveloper/desarrollo/archivos/Categoria/Logo/",
       "arcextension": ".png",
       "arcestado": "Activo",
       "arceliminado": "No",
     },     
     "palid": 1,
     "catnivel": 0,
     "catpadre": "null",
     "cattestado": "Activo",
     "catelimcatado": "No",
     "catreferencia": "Tecnologia"
   } 
 ]
