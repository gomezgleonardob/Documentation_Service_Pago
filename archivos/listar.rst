.. index::
   single: listar

LISTAR
------

Esta transacción recibe la petición filtrar una oferta

* Moneda.
* Valor de la oferta.
* Fecha de entrega.

JSON IN
~~~~~~~

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
~~~~~~~
.. tabularcolumns:: |p{1cm}|p{7cm}|

.. csv-table:: Fitros
   :file: archivos/csv/atributos.csv
   :header-rows: 1
   :class: longtable
   :widths: 1 1

JSON OUT
~~~~~~~~