**1. Resumen de Resultados**

| Tipo de Prueba | Total de Casos | Ejecutados | Exitosos | Fallidos |
| -------------- | -------------- | ---------- | -------- | -------- |
| Funcionales    | 6              | 6          | 6        | 0        |
| Negativos      | 4              | 4          | 3        | 1        |
| Regresion      | 6              | 6          | 6        | 0        |
| Total General  | 16             | 16         | 15       | 1        |


**2. Casos Fallidos**

1. Caso: Pago con tarjeta invalida.
	* Precondiciones: El usuario ingresa un numero de tarjeta incorrecto.
	* Resultado esperado: La transaccion es rechazada con un mensaje apropiado.
	* Resultado: El sistema muestra un mensaje generico. ("Error en el pago");
	* Impacto: Moderado. No afecta el sistema pero es una mala experiencia. 

**3. Observaciones Clave**

* Mensaje de Error: Los mensajes de error no fueron especificaos para una tarjeta invalida. 
* Impacto General: La mayoria de ls casos funcionales fueron exitosas, pero debemos mejorar la claridad de los mensajes y mejorar la experiencia del usuario. 

**4. Metricas**
* Porcentaje de exito: 95%
* Tiempo total de Ejecuccion: 20 minutos.
* Cubertura de Prueba: 100% de los casos fueron ejecutados. 

**5. Recomendacione**
1. Mejorar los mensajes de error con pagos fallidos. 
2. Realizar pruebas adicionales en QA como se seguridad y peformance. 