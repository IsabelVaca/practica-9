# Bitácora — Práctica 9: Tareas + Hilt

## Ejercicio A2 — ¿Qué tendrías que cambiar?
*(en parejas · 4 min · sin escribir código)*

Con el starter abierto, y sin editar `ApiRemota`: ¿qué archivos tocarías para que la app muestre solo «Tarea de prueba»? ¿Y cómo regresarías a los datos reales?

Quitar la llamada a la API para que salga la lista fija: se toca solo la implementación del repositorio (el que hace de "enchufe falso"), reemplazando la llamada a `ApiRemota` por el retorno directo de la lista con «Tarea de prueba». Para volver a los datos reales, basta con revertir ese cambio y dejar que el repositorio vuelva a llamar a `ApiRemota`.

## Ejercicio E1 — ¿Por qué bastó una línea?
*(3 min · por escrito)*

¿Cuántos archivos cambiaste? ¿Cuántos habrías cambiado en el starter para lograr lo mismo? ¿Por qué ni el ViewModel ni la pantalla se enteraron?

Basta con cambiar un solo archivo: el repositorio falso, que solo devuelve la lista fija de prueba en vez de llamar a la API. En el starter (sin Hilt ni interfaz) habría que tocar varios archivos, porque la llamada a la API estaría mezclada con la lógica de la pantalla o del ViewModel. Aquí no fue así porque `TareasRepository` es la interfaz —el "enchufe"— y el resto de las partes (ViewModel, pantalla) no saben de dónde viene la información, solo la reciben.

## Ejercicio E2 — Boleto de salida
*(3 min)*

**¿Qué es inyección de dependencias?**
Es una forma de darle a una clase lo que necesita para funcionar sin que ella misma lo construya, para poder correrlo en tu compu (o en pruebas) sin que esa dependencia "viaje" fija hasta la app.

**¿Para qué sirve la interfaz `TareasRepository`?**
Para pasar los valores deseados al ViewModel: define el contrato de cómo se obtienen los datos, sin que el ViewModel sepa si vienen de una API real o de una lista fija de prueba.

**¿Qué hace `@Binds` en un módulo de Hilt?**
Conecta una interfaz con su implementación concreta, indicándole a Hilt cuál clase debe usar cuando algo pide esa interfaz.
