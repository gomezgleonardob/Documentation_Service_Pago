.. index::
   single: introduccion

Introducción
============


El presente documento contiene un detalle de las transacciones soportadas por el microservicio ESB. Este microservicios es un enrutador que recibe parametros y se encarga de enrutar al modulo que correspondiente.
Este servicio es un web service REST el cual recibe la información a traves del metodos POST,  y  tiene una función “ejecutar”, el cual recibe como parámetro de entrada una cadena string en formato json codificada en 128 bits  y la respuesta es una cadena en formato JSON sin codificar.  Los datos de entrada y salidas son específicos por cada tipo de proceso.

    • **Protocolo**: Para pruebas se usa http y para producción https.

    • **IpServidor**: Ip o Url de producción solicitar a la persona encargada del modulo ESB.

    • **ClaveAcceso**: Código de referencia unico por transaccion.

    • **Aplicacion**: Tipo de plataforma desde donde se realiza la transacción ejemplo Chrome, Mozilla, Android, IOS, etc
    
    • IdAplicacion: Id del dispositivo desde donde se realiza la transacción en los navegadores web enviar “browser-firefox|version-63.0.0|so-Windows10” dependiendo del navegador y en los dispositivos moviles enviar el id del dispositivo.
    • Menu: El menu hace referencia al microservicio que vamos a llamar y sobre la entidad que vamos a trabajar ejemplo: seguridad.Usuario donde seguridad es el microservicio que administra la seguridad del sistema este debe ir siempre en minusculas y Usuario es la entidad o modelo sobre el cual se va a realizar la transacción la primera letra debe ir en mayuscula.
    • Accion: Nombre de la acción a ser realizar por ejemplo listar, crear, modificar estas transacciones deben ser especificadas en cada modulo.
    • Abreviatura: iniciales de la tabla o entidad sobre las cuales se va a realizar la operación ejemplo si voy listar persona la apreviatura es per
    • Nombreclase: Nombre de la clase sobre la cual se va realizar la operación por ejemplo GenericDao, este nombre debe estar especificado en la documentación del cada modulo.
    • Ip: ip del usuario que realiza la petición
