# Api Seguimiento de pedidos 
Api de tipo REST de la cual se obtiene los folios de todo el proceso de documentos de en qué etapa va desde el folio de pedido, hasta la factura a la donde estará referenciada ese pedido 
proporciona la clave del cliente fecha y hora de la facturación 



# URL:
http://sprautomotive.servehttp.com:9090/seguimientopedidosapp
http://sprautomotive.servehttp.com:9095/seguimientopedidosapp
http://sprautomotive.servehttp.com:9080/seguimientopedidosapp

# Método:
Post

# HEADERS:
user: usuario
pass: contraseña

# Body(form_data)
* ### (Obligatorio) fechainicial
* ### (Obligatorio) fecha final
* ### cliente:
  Mandar la clave del cliente para obtener de un cliente en específico o si se requiere dejar vacío para que mande todos los clientes 
* ### (Obligatorio) vendedor:
 Mandar la clave de vendedor para que traiga clientes solo de tu cartera 

```
$response = $curl->get("sprautomotive.servehttp.com:9095/seguimientopedidosapp?{$params}", ['headers' => $headerdatosproducto]);

$params= ?fechainicial=2025-5-1&fechafinal=2025-06-03&cliente=&vendedor=203;


$headerdatosproducto;

$headerdatosproducto= array(
            'Accept' => 'application/json',
            'user' =>'Usuario'
            'pass' =>'Contraseña');
//se recibe con
$response = collect(json_decode($response->getBody()))
```
Si la solicitud es correcta recibiremos la siguiente respuesta:
```

  {
    "Item": {
        "0": {
            "k_Pedido": "0032589",
            "k_FECHA_PED": "2025-05-02",
            "k_CLIENTE": "20521",
            "k_LIBERACION": "0032449",
            "k_ADUANA": "0032356",
            "k_FACTURA": "0026857",
            "k_FECHA_FACT": "2025-05-02",
            "k_HORA": "A153382",
            "k_FOLIOWEB": "10:08"
        }
    }
}
```
Los valores son los siguientes
* ### Item: Ejemplo del Items siendo un Array conteniendo su información adentro de este mismo
*### 0,1,2…N: El consecutivo de cada Item
### Donde aloja dos objetos que son el precio y la existencia y línea.

  * ### k_Pedido: Folio del pedido.
  * ### k_FECHA_PED: Línea a la que pertenece.
  * ### k_CLIENTE : Clave de Cliente
  * ### k_LIBERACION: Folio liberación
  * ### k_ADUANA: Folio Aduana
  * ### k_FACTURA: Folio Factura
  * ### k_FECHA_FACT: Fecha de la Factura emitida
  * ### k_HORA: Hora de la Factura emitida
  * ### k_FOLIOWEB: Folio de la página web.

  De llegar a tener algún error el formato mandara un Objeto Vacío
  ```
  {}
  ```
# Usuario y Contraseña Deshabilitado o error en ella 
En dado caso de tener un usuario o contraseña con problemas Obtendrás el siguiente error
de esta forma podrás comunicarte con tu proveedor y intentaremos apoyarte con tu problema.
```
{
    "ok": "0",
    "err": "Unauthorized user or incorrect password."
}
```

  
