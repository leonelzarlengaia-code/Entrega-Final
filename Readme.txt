README - Workflow Automatizado de Videojuegos

Descripción:
Este workflow automatiza la obtención de videojuegos desde una API, filtra los datos, los guarda en una hoja de cálculo y envía un correo electrónico generado automáticamente según el tipo de juego.

Funcionamiento paso a paso:

1. Ejecución automática
   El workflow se inicia mediante un disparador programado (Schedule Trigger) que se ejecuta cada 10 minutos.

2. Obtención de datos
   Se realiza una solicitud HTTP a la API de videojuegos:
   https://www.freetogame.com/api/games
   Esto devuelve una lista de juegos disponibles.

3. Selección aleatoria
   Se ejecuta un script que selecciona un juego al azar de la lista obtenida.

4. Preparación de datos
   Se extraen y organizan los siguientes datos del juego:

* Título
* Descripción
* Género
* Fecha de lanzamiento
* Plataforma

5. Filtro por plataforma
   Se verifica si el juego pertenece a la plataforma "PC (Windows)".

* Si no cumple, se vuelve a intentar con otro juego.
* Se lleva un contador de intentos.

6. Guardado en Google Sheets
   Si el juego cumple la condición, se guarda en una hoja de cálculo con los datos correspondientes.

7. Control de intentos
   Se incrementa un contador cada vez que se intenta seleccionar un juego.
   Si el contador llega a 10 intentos, el proceso se detiene.

8. Lectura de datos
   Se leen los datos guardados en la hoja de cálculo.
   Se ordenan y se selecciona el último registro agregado.

9. Clasificación con IA
   Se analiza el género del juego utilizando un modelo de inteligencia artificial.

* Si el género es relevante (Shooter, RPG, Estrategia, etc.), se clasifica como POSITIVO.
* En caso contrario, como NEGATIVO.

10. Decisión del flujo
    Según el resultado:

* POSITIVO: se genera un email promocional.
* NEGATIVO: se genera un email más simple o persuasivo.

11. Generación del email
    Se utiliza IA para crear:

* Asunto
* Cuerpo del mensaje

12. Envío de correo
    Se envía el email automáticamente mediante Gmail.

Resumen:
El sistema automatiza la búsqueda, filtrado y análisis de videojuegos, y genera correos electrónicos personalizados sin intervención manual.

Tecnologías utilizadas:

* n8n
* API FreeToGame
* Google Sheets
* Google Gemini (IA)
* Gmail
* Se necesitan credenciales de: Google Sheets, Google Gemini y Google Gmail. 

.
