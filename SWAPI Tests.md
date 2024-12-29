
**B. Personaje con id 99.**
End point: `api/people/99`

Al intentar acceder al endpoint `api/people/99` recibo un error: 

```
{

“Message”: “not found”

}
```
Segun las lista de personajes, hay un total de 82 records y 9 paginas. Usando los parameters page=9&limit=10, me da los ultimos resultados y el ultimo uid=83


**C. Numero Maxima de Personas**
End point: `/api/people
`
El numero maximo lo obtengo de 2 formas, la primera es usando la propiedad `total_records` que viene en el body del endpoint `/api/people` y la otra es obtendiendo el length del array dentro de la propiedad “results” las dos tienen un valor de 82.

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