.. index::
   single: solicitud

SOLICITUD
=========


 El usuario crea la solicitud y puede llevar los siguientes elementos

    • La solicitud lleva foto y el link.
    • La solicitud lleva foto  
    • La solicitud lleva el link

JSON IN 
~~~~~~~

.. code-block:: javascript

  { 
     "detail": [
      {
         "objeto": {
         "usuid": "db97b24be40c3d68ebec588209e41b36",
         "catid": "9ca40f9be9423c169f395626f80e3c07",
         "dirid": "25296619b814452080f7ae451309b545",
          "arcid": {
          "arcid": "",
          "arcnombre": "",
          "arcruta": "engideveloper/desarrollo/archivos/Categoria/Logo/",
          "arcextension": "png",
          "archivob64": "W3j3QHli8OYN"
         },
          "sollink": "https://www.ebay.com/itm/NVIDIA-GeForce-GTX....",
          "soldescripcion": "GPU",
          "solindicaciones": "Comprar la de 6GB"
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

JSON IN 
~~~~~~~

Lleva solo la imagen

{
"detail":[
{
"objeto":{
"usuid":"db97b24be40c3d68ebec588209e41b36",
"catid":"9ca40f9be9423c169f395626f80e3c07",
"dirid":"25296619b814452080f7ae451309b545",
"arcid":{
"arcid":"",
"arcnombre":"",
"arcruta":"engideveloper/desarrollo/archivos/Categoria/Logo/",
"arcextension":"png",
"archivob64":"iVBORw0KGg..”
},
"sollink":"",
"soldescripcion":"GPU",
"solindicaciones":"Comprar la de 8GB/MOLEx"
}
}
],
"generarid":true,

Los datos de entrada deben ser en formato JSON y codificados en AES 128 bits,esta codificación esta basada en dos clave, clave de encriptación y clave del vector de inicialización. Estas claves deben ser brindadas se configuran en el properties engiAcceso.properties.