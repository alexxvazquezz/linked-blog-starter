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
End point: `/api/planets/27`

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

