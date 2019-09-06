.. index::
   single: crear

ACTUALIZAR
==========

Esta transacción recibe la petición  para actualizar  una oferta , luego se enruta hacia el microservicio correspondiente y responde en un objeto con formato JSON.

Los atributos que se pueden actualizar son :

* Moneda.
* Valor de la oferta.
* Fecha de entrega.

JSON IN
-------

.. code-block:: javascript

{

      {

    "limit":"10",
    "orderby":"",
    "filtro":{
        "ofertaPK":{
            "ofeid":"",
            "viaid":"",
            "solid":""
        },
        "ofeestado":"Activo"
    },
    "usuario":{
        "usuid":"1",
        "usuclave":"21232f297a57a5a743894a0e4a801fc3",
        "usuverificado":1,
}
..




FILTROS
-------


JSON OUT
--------