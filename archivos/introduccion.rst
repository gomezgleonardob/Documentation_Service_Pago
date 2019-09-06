.. index::
   single: introduccion

Introducción
============


El presente documento contiene un detalle de las transacciones soportadas por el microservicio ESB. Este microservicios es un enrutador que recibe parametros y se encarga de enrutar al modulo que correspondiente.
Este servicio es un web service REST el cual recibe la información a traves del metodos POST,  y  tiene una función “ejecutar”, el cual recibe como parámetro de entrada una cadena string en formato json codificada en 128 bits  y la respuesta es una cadena en formato JSON sin codificar.  Los datos de entrada y salidas son específicos por cada tipo de proceso.

