.. index::
   single: pago

PAGO
====

Esta transacción recibe la petición  para actualizar  una oferta , luego se enruta hacia el microservicio correspondiente y responde en un objeto con formato JSON.

Los atributos que se pueden actualizar son :

* Moneda.
* Valor de la oferta.
* Fecha de entrega.

JSON IN
~~~~~~~

.. code-block:: javascript

{
    "detail": [
        {
            "objeto": {
                "ofertaPK": {
                    "ofeid": "",
                    "viaid": "8577325c12d271c28ca1d58e31ae0578",
                    "solid": "sol1"
                },
                "monid": 2,
                "ofevalor": 300,
                "ofetraida": 150,
                "ofefechaentrega": "2019-08-10"
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


ATRIBUTOS
~~~~~~~~~

.. tabularcolumns:: |p{1cm}|p{7cm}|

.. csv-table:: Fitros
   :file: archivos/csv/atributos.csv
   :header-rows: 1
   :class: longtable
   :widths: 1 1
.. 

JSON OUT
~~~~~~~~


