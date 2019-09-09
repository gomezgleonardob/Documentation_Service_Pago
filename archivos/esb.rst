.. index::
   single: esb

MICROSERVICIO ESB
=================

Este servicio es un web service REST el cual recibe la información a través de una petición POST,  y  tiene una función “ejecutar”, el cual recibe como parámetro de entrada una cadena string en formato json codificada en 128 bits  y la respuesta es una cadena en formato JSON sin codificar.  Los datos de entrada y salidas son específicos por cada tipo de proceso.

PARÁMETROS DEL MICROSERVICIO
----------------------------

.. csv-table:: a title
   :header: "Campo", "Descripción"
   :widths: 40, 500

    "Protocolo", "Para pruebas se usa http y para producción https."
    "IpServidor", "Ip o Url de producción solicitar a la persona encargada del modulo ESB."
    "ClaveAcceso", "Clave única de acceso."
    "Aplicacion"," Tipo de plataforma desde donde se realiza la transacción ejemplo Chrome, Mozilla, Android, IOS."
    "IdAplicacion", "Id del dispositivo desde donde se realiza la transacción ejemplo: “browser-firefox|version-63.0.0|so-Windows10” desde un navegador web.."
    "Menu", "El menú hace referencia al microservicio que vamos a llamar y sobre la entidad que vamos a trabajar ejemplo: seguridad.Usuario donde seguridad es el microservicio que administra la seguridad del sistema este debe ir siempre en minúsculas y Usuario es la entidad o modelo sobre el cual se va a realizar la transacción la primera letra debe ir en mayúscula."
    "Abreviatura", "iniciales de la tabla o entidad sobre las cuales se va a realizar la operación ejemplo si voy a listar persona la abreviatura es per."
    "Nombreclase"," Nombre de la clase sobre la cual se va a realizar la operación por ejemplo GenericDao, este nombre debe estar especificado en la documentación del cada módulo."
    "Ip", "Ip del usuario que realiza la petición."
..

TRANSACCIONES
-------------

Una de las transacciones que se puede realizar con el microservicio es: 

EJECUTAR
^^^^^^^^

Para ejecutar la microtransacción se envía un objeto JSON codificado en AES 128 , el vector de inicialización y la clave debe ser proporcionado.

**URL**

La siguiente url es la que se usa para codificar y decodificar la trama de json.

.. _AES: https://www.devglan.com/online-tools/aes-encryption-decryption

**JSON IN**

..code-block:: javascript

{
  "detail": [],
  "limit": "100",
  "orderby": "",
  "filtro": {},
  "usuario": {
    "usuid": "1",
    "usuclave": "21232f297a57a5a743894a0e4a801fc3",
    "perid": {
      "perid": "1",
      "percorreo": "jeisson.millos@hotmail.com",
      "sexid": 1
    },
    "lenid": "es"
  },
  "rol": {
    "rolid": 1
  }
}


CATALOGO DE RESPUESTA
^^^^^^^^^^^^^^^^^^^^^

.. csv-table:: a title
   :header: "CÓDIGO", "DESCRIPCIÓN"
   :widths: 40, 100

    "Protocolo", "Para pruebas se usa http y para producción https".
    "IpServidor", "Error: solo se permiten archivos .png, .jpg o jpeg".

..