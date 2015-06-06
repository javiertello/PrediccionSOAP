# Servicio SOAP de predicción meteorológica

Los servcios a publicar se encuentran en la clase Services, como indica el fichero `deploy_proyecto.wsdd`, para desplegarlo.

El servicio ofrece las siguientes operaciones:

> __DescargarInfoTiempo__: Recibe como parámetro un XML que contiene el ID de una ciudad, devuelve el XML con la predicción meteorológica, descargado del **aemet**.
Ejemplo de Request decodificado de Base64:

`<?xml version=\"1.0\" encoding=\"UTF-8\"?>
	<!DOCTYPE id [					
	<!ELEMENT id (#PCDATA)>
]>
<id>50257</id>`

Ejemplo de Response decodificado de Base64:

`<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<!DOCTYPE resultado [
<!ELEMENT resultado (#PCDATA)>
"]>
<resultado>xml_prediccion_base64</resultado>`


> __GenerarJSON__: Recibe como parámetro el xml de predicción meteorológica, y lo devuelve transformado a formato JSON.

Ejemplo de Request decodificado de Base64:

`<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<!DOCTYPE aemet [
	<!ELEMENT aemet (#PCDATA)>
"]>
<aemet>xml_prediccion_base64</aemet>`

Ejemplo de Response decodificado de Base64:

`<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<!DOCTYPE resultado [
	<!ELEMENT resultado (#PCDATA)>
"]>
<resultado>json_prediccion_base64</resultado>`


> __GenerarHTML__: Recibe como parámetro el XML o JSON de predicción meteorológica, y devuelve el código HTML de la tabla de predicción en los 3 próximos días.


Ejemplo de Request decodificado de Base64:

`<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<!DOCTYPE raiz [
	<!ELEMENT raiz (formato, content)>
	<!ELEMENT formato (#PCDATA)>
	<!ELEMENT content (#PCDATA)>
]>
<raiz>
	<formato>json o xml</formato>
	<content>base64json o base64xml</content>
</raiz>`

Ejemplo de Response decodificado de Base64:

`<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<!DOCTYPE resultado [
	<!ELEMENT resultado (#PCDATA)>
"]>
<resultado>html_prediccion_base64</resultado>`

