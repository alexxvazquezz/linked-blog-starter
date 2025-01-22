A. Naves 
End point: /api/starships

Aca no hubo ningun inconveniente. 

![[Screenshot From 2024-12-31 11-55-15.png]]

**B. Personaje con id 99.**
End point: `api/people/99`

Al intentar acceder al endpoint `api/people/99` recibo un error: 

```
{

“Message”: “not found”

}
```
Segun las lista de personajes, hay un total de 82 records y 9 paginas. Usando los parameters page=9&limit=10, me da los ultimos resultados y el ultimo uid=83
![[Screenshot From 2024-12-31 11-56-40.png]]


**C. Numero Maxima de Personas**
End point: `/api/people
`
El numero maximo lo obtengo de 2 formas, la primera es usando la propiedad `total_records` que viene en el body del endpoint `/api/people` y la otra es obtendiendo el length del array dentro de la propiedad “results” las dos tienen un valor de 82.

![[Screenshot From 2024-12-31 12-02-55.png]]

![[Screenshot From 2024-12-31 12-03-55.png]]


D. Propiedades Planeta con ID 27
End point: `/api/planets/27
`
En este caso, se selecciono un id de planeta para obtener sus propiedades. 
```json
"properties": {
	"diameter": "14050",
	"rotation_period": "26",
	"orbital_period": "334",
	"gravity": "1 standard",
	"population": "4000000000",
	"climate": "temperate",
	"terrain": "plains, seas, mesas",
	"surface_water": "10",
	"created": "2024-12-27T20:40:22.731Z",
	"edited": "2024-12-27T20:40:22.731Z",
	"name": "Ord Mantell",
	"url": "https://www.swapi.tech/api/planets/27"
}
```
![[Screenshot From 2024-12-31 12-09-11.png]]
E. Schema de Recursos
Endpoint Species: /api/species/id
Endpoint Vehicles: /api/vehicles/id

### Species

| Field            | Type             | Description                                               |
| ---------------- | ---------------- | --------------------------------------------------------- |
| classification   | string           | Classificacion de la esecie, como mamifero                |
| disignation      | string           | Status de sentient                                        |
| average_height   | string           | La altura promedia en cm                                  |
| average_lifespan | string           | La vida promedio en anos                                  |
| hair_colors      | string           | Lista de tipo de colores de pelo                          |
| skin_colors      | string           | Lista de colores de piel                                  |
| eye_colors       | string           | Lista de colores de ojos                                  |
| homeworld        | string           | URL de la madre tierra de la especie                      |
| language         | string           | El idioma primario de esta especie                        |
| people           | array of strings | URL's de individuos que son de esta especie               |
| created          | string           | Timestamp de creacion del recurso                         |
| edited           | string           | Timestamp de ultima modificacion del recurso              |
| name             | string           | Nombre de la espcie.                                      |
| url              | sttring          | URL de esta especie                                       |
| description      | string           | Una discripcion de la especie                             |
| _id              | string           | Identificador  para la especie                            |
| uid              | string           | Identificador unico de la especie                         |
| __v              | number           | El version key para el recurso. Usado en la base de datos |
Observaciones: 
* El campo 'Films' no esta en el body del response, aunque le documentacion especifica que es parte. 
* Este comportamiento persiste aun usando la specie con  nombre "Wookie", que es el ejemplo en la documentacion
* `people` y `homeworld` es una lista de urls que linkean a otros recursos
* `name` y `uid` son idenficadores unicos para la specie

### Vehicles

| Field                  | Type    | Description                                      |
| ---------------------- | ------- | ------------------------------------------------ |
| uid                    | string  | Identificador unico                              |
| name                   | string  | Nombre del vehiculo                              |
| model                  | string  | Modelo del vehiculo                              |
| manufacturar           | string  | Constructor de vehiculo                          |
| cost_in_credits        | string  | Costo del vehiculo en creditos                   |
| length                 | string  | El largo del vehiculo                            |
| max_atmosphering_speed | string  | Maxima velocidad del vehiculo segun la atmosfera |
| crew                   | string  | La cantidad de tripulantes requeridos            |
| passengers             | string  | La cantidad de pasajeros que puede llevar        |
| cargo_capacity         | string  | La capacidad del cargamento                      |
| consumables            | string  | La cantidad de consumibles                       |
| vehicle_class          | string  | La clase o tipo de vehiculo                      |
| pilots                 | array   | Una lista de URL's de los pilotos                |
| films                  | array   | Una lista de URL's de las peliculas              |
| created                | string  | Fecha cuando fue creado en la base de datos      |
| edited                 | string  | Fecha cuando fue modificado                      |
| url                    | string  | La URL del recurso del vehiculo                  |
| description            | string  | Una descripcion del vehiculo                     |
| _id_                   | string  | ID interno                                       |
| __v                    | integer |                                                  |


Observaciones:
* La lista de films y pilotos vuelve vacia en algunas ocaciones. Para crear tests hay que tomarlo en cuenta. Tambien hay que hacer tests que validan los detalles de los datos dentro de las URLS's
* El campo consumable tiene un valor de 'none'. 
* El campo cost_in_credits llama la atencion por vovler un 'unknown', hay que tomar en cuenta esto para crear tests. 

Response Body Species:
![[Screenshot From 2024-12-31 12-14-10.png]]
Response Body Vehicle:
![[Screenshot From 2024-12-31 12-14-26.png]]

f. ID del Film
End point: `/api/films/`
Parameters: `/api/films/?title={title}`

Para obtener el id del film con el titulo, se utilizo los parametros para la busqueda segun el su nombre de titulo. El parametro es `?title=The Phantom Menace`. 
Para obtener el ID, se escribio un script para que se visualice en la consola:
```
const jsonData = pm.response.json();

const filmId = jsonData.result[0].properties.episode_id;

console.log('Film id: ', filmId);
```
![[Screenshot From 2024-12-31 12-21-37.png]]

g. Consulta en Formato Wookiee
En este escenario el encoding vuelve en un string del mismo json object. Para poder visualizar el nombre se tuvo que parsar a json dos veces. Abajo esta el script:
```
let body = pm.response.text();

  

let parsedJson = JSON.parse(body);

  

let wookieeBody = JSON.parse(parsedJson);
```
Y para visualizar el nombre en la cosola, se agrego estas dos lineas:
```
let wookieeName = wookieeBody.akrcooakworcaoahwoc.whrascwo;

  

console.log("Wookie name:", wookieeName);
```
![[Screenshot From 2024-12-31 12-32-04.png]]

## Preguntas Adicionales
1. Para automatizar el api, aprovecharia el runner de postman. Ya que se esta utilizando esta herramienta. Pero, prefereria centralizar todo, los tests de UI y API, usando cypress. 
2. Pruebas:
	Data:
		a. Validacion de status codes: 200, 201, etc
		b. Verificar que cada body tiene la estructura de datos y campos correctos.
		c. Pruebas con parametros opcionales, como las de busqueda
		d. Validar que la dara es del typo correcto, `string`, `array`, `number`.
		e. Verificar los recursos adicionales, URL's.

	 Performance:
	  a. Medir el tiempo de respuesta
	  b. Medir el api con datasets grandes, por ejemplo el maximo pagination. 
	  c. Testear llamadas concurrentes para validar si puede manejar multiples usuarios
	  d. Validar el rate limiter. 

	 Edge Cases:
	  a. Parameters faltantes
	  b. Types de datos incorrectos en los parametros
	  c. Valore de parametros fuera de rango. -1, 10000. 
	  d. Hacer un request con un recurso que no existe. Un id de personaje que  no existe. 
	  e. Test con parametros duplicados

   Error Handling:
     a. 404 not found
     b. 400 bad request
     c. 401 unauthorized
     d. 500 internal error