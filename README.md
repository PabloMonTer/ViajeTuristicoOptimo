# ViajeTuristicoOptimo
Generación de ruta optima de viaje a lugares turísticos en Nayarit por medio de la programación lineal en Python.



## 1. Modelado del Problema}
1. Modelado del Problema
El TSP fue formulado como un problema de programación lineal (PL). Para ello, se construyó una matriz de costos que representa la distancia o el costo entre cada par de ciudades. La matriz fue creada de manera que cada entrada representa el costo de viajar de la ciudad i a la ciudad j.

## 2. Uso de la librería PuLP
Se utilizó la librería PuLP para definir y resolver el problema de programación lineal. PuLP permite la formulación de problemas de optimización de manera sencilla y eficiente. En este caso, el objetivo es minimizar el costo total del recorrido, sujeto a ciertas restricciones que aseguran la validez de la solución.

## 3. Restricciones
Las restricciones del modelo fueron las siguientes:

 -Restricción de un solo recorrido por ciudad: Cada ciudad debe ser visitada exactamente una vez. Esto se logra con la restricción de que para cada ciudad, solo puede existir una salida y una entrada.

 -Restricción de ciclo: Para evitar que la solución contenga ciclos subóptimos (por ejemplo, un ciclo que no visite todas las ciudades), se agregó una restricción basada en variables adicionales (subtour elimination). Esta restricción garantiza que no se formen ciclos menores a la ruta completa.

## 4. Solución
Una vez formulado el problema, se resolvió utilizando el solver de PuLP. El resultado es la ruta óptima, que minimiza el costo total del recorrido. El modelo también devuelve la secuencia de ciudades que debe seguir el vendedor para lograr la mínima distancia total.
