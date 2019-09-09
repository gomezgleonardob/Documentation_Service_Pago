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
    "Aplicacion","Tipo de plataforma desde donde se realiza la transacción ejemplo Chrome, Mozilla, Android, IOS."
    "IdAplicacion", "Id del dispositivo desde donde se realiza la transacción ejemplo: “browser-firefox|version-63.0.0|so-Windows10” desde un navegador web.."
    "Menu", "El menú hace referencia al microservicio que vamos a llamar y sobre la entidad que vamos a trabajar."
    "Abreviatura", "Iniciales de la tabla o entidad sobre las cuales se va a realizar la operación ejemplo si voy a listar persona la abreviatura es per."
    "Nombreclase","Nombre de la clase sobre la cual se va a realizar la operación por ejemplo GenericDao, este nombre debe estar especificado en la documentación del cada módulo."
    "Ip", "Ip del usuario que realiza la petición."
..

TRANSACCIONES
-------------

Una de las transacciones que se puede realizar con el microservicio es: 

EJECUTAR
^^^^^^^^

Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encryptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties

Atributos
~~~~~~~~~

.. csv-table:: a title
   :header: "Código", "Descripción"
   :widths: 40, 500

     "Detail","Se envía un array de objetos sobre los cuales se vaya a realizar una operación".
     "Limit","Esta propiedad se usa cuando se realiza transacciones para listar y se envía solo el numero ejemplo 100, esto me va a traer un máximo de 100 resultados."
     "Orderby","Esta propiedad se usa cuando se realiza transacciones para listar y se envia la o las columnas separadas por una sola coma, ejemplo menuid, menunombre"
     "Filtro","Se envía el objeto sobre el cual se esta realizando una consulta del tipo listar, si se esta listado el listado de usuarios"
     "Usuario", "Se debe enviar el objeto usuario que esta realizando la transacción, solo en el caso de login este objeto no se debe enviar."
     "Rol","Se debe enviar el objeto rol con el cual se realiza la transacción, este es usado para validar si un usuario tiene permiso de realizar una acción. Dependiendo la acción se solicitará este valor."

..

**JSON IN**

.. code-block:: javascript


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

**URL**

La siguiente url es la que se usa para codificar y decodificar la trama de json.

`Codifación/Decodificación <https://www.devglan.com/online-tools/aes-encryption-decryption/>`_

CATALOGO DE RESPUESTA
---------------------

.. csv-table:: a title
   :header: "Código", "Descripción"
   :widths: 40, 500

    "success000","Transacción Exitosa"
    "error001","Error: Error de ingreso de información"
    "error002","Error: Error al modificar"
    "error003","Error: Error al activar"
    "error004","Error: Error al desactivar"
    "error005","Error: Error al eliminar"
    "error006",Error: Error al listar"
    "error007,"Error: Permisos Insuficientes"
    "error008","Error: Datos no validos"
    "error009","Error: la clave ingresada no es la correcta"
    "error010","Error: Código no valido"
    "error011","Error: Sin archivo de configuración"
    "error012","Error al subir archivo"
..


