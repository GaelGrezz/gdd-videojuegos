# Alcance

## Descripción de la sección

Define qué se va a construir y, sobre todo, qué queda fuera del proyecto.

## Alcance de la primera versión

La primera entrega usa las funciones que ya están integradas en Unity. Las pruebas de entrega se centran en ese contenido y en el flujo jugable actual.

### Incluido

- Un solo nivel, el centro científico de Hades, con 10 minutos de supervivencia y el combate contra el Ascendido.
- Linterna y batería, arma inicial, generadores y director de IA por tickets.
- Dos enemigos regulares, la Cáscara y la Quimera, y un jefe final, el Ascendido.
- Cristales, subida de nivel, mejoras, rachas y potenciadores.
- Regeneración de la salud después de recibir daño.
- Nicolás e Issac, los registros de los operativos fallecidos y los finales *Información recuperada* y *Ni uno más*.
- Menú principal, carga, HUD, pausa, selección de mejoras, Opciones, Créditos, Victoria y Game Over. Los registros se leen en el panel de comunicaciones. Se incluyen la música y los efectos de sonido ya integrados. Véase [[02 - UI y Menús]].

### No incluido

- Multijugador local o en línea.
- Tienda, moneda y botiquines.
- Progreso entre partidas.
- Otras plataformas, control y pantalla táctil.
- Niveles, capítulos o mapas adicionales.

### Versiones posteriores

- Archivo del jugador como pantalla independiente, estructuras defensivas nuevas e invocaciones del Ascendido.
- Modelo retro definitivo del Ascendido, aviso sonoro de batería baja y sonidos del jefe que todavía faltan.
- Aplicación de los ajustes pendientes de Opciones, incluidos brillo, filtro VHS, tamaño de texto, subtítulos y volumen de futuras voces. También quedan para después las opciones de accesibilidad aún sin integrar.
- Migración de los datos de balance a `ScriptableObject`. Las cartas activas ya usan ese formato.

## MVP

El MVP de AfterLight es una partida de supervivencia para un jugador en Windows, con teclado y mouse. Parte del flujo ya integrado en Unity, desde `MenuPrincipal.unity` hasta `CentroHades.unity` y el resultado de la partida.

### Bucle principal

- El jugador inicia el despliegue desde el menú. Al terminar la carga, controla a Eco-10 en el centro científico de Hades.
- Usa la linterna para debilitar enemigos, dispara y recarga el rifle inicial, y repara o defiende los tres generadores para recargar la batería. La salud se regenera tras un periodo sin recibir daño.
- El director introduce Cáscaras y Quimeras mediante tickets. El jugador recoge cristales, elige mejoras al subir de nivel y obtiene potenciadores por racha.
- A los 10 minutos de juego activo aparece el Ascendido con su modelo de primitivas. El jugador debe derrotarlo para obtener *Información recuperada*. Si se agota la salud o el margen con la batería vacía, se abre directamente Game Over con *Operativo caído* o *Sin luz*.
- El HUD muestra el estado de la partida. El flujo incluye pausa, selección de mejoras y pantallas de resultado con las acciones disponibles de reintentar o volver al menú.

### Contenido opcional integrado

Los 28 registros y la cadena de Issac están disponibles en el mismo nivel. Si el jugador completa sus peticiones y derrota al Ascendido, obtiene *Ni uno más*. El jugador puede completar una partida por la ruta principal sin seguir esa cadena.

### Validación del MVP

- [ ] Iniciar desde el menú, cargar Hades, reparar un generador, recargar batería y elegir una mejora. Comprobar que la pausa y la selección de cartas detienen el reloj.
- [ ] Jugar hasta los 10 minutos sin atajos de desarrollo y derrotar al Ascendido para obtener *Información recuperada*.
- [ ] Provocar cada causa de derrota y verificar *Operativo caído*, *Sin luz* y que Reintentar inicia una partida desde cero.
- [ ] Completar la cadena de Issac en otra partida y verificar *Ni uno más*.

El alcance está definido. Los resultados de ejecución se registran en [[02 - Pruebas]].

## Vertical Slice

La muestra jugable para la primera entrega es la misma partida en Hades con el kit de CERBERUS, Eco-10 animado, la interfaz y el audio ya integrados, y el Ascendido con su modelo de primitivas. Se valida con los casos del MVP.

## Criterios de recorte

La primera entrega se prepara con el perfil actual de compilación para Windows. Las propuestas y acabados futuros quedan registrados en el [[04 - Backlog del Proyecto]]. Los defectos del contenido integrado se siguen en [[03 - Bugs y Seguimiento]].


> **Navegación:** [[00 - Índice]] · ← [[05 - Seguridad y Riesgos Técnicos]] · [[02 - Roles y Responsabilidades]] →
