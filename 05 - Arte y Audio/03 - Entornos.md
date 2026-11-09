# Entornos

## Descripción de la sección

Define la estética y necesidades visuales de escenarios, fondos, objetos y elementos ambientales.

## Zonas

| Zona | Estilo | Elementos | Función |
|---|---|---|---|
| Acceso principal | Industrial, con puertas pesadas y señalización de CERBERUS | Hojas de puerta, marcas de piso, cajas y señal de sector | Presentar la entrada y los controles básicos |
| Áreas de combate y circulación | Pasillos modulares de concreto y metal pintado, en penumbra | Muros, columnas, postes, tuberías y paneles | Sostener los enfrentamientos y conectar sectores |
| Puntos de generadores | Salas técnicas iluminadas por el generador | Generador, marcas de peligro, paneles y tuberías | Concentrar las decisiones de reparación y defensa |
| Laboratorios y sectores secundarios | Instalaciones científicas abandonadas, con rastros de sus ocupantes | Por definir | Alojar exploración y registros |
| Punto o medio de contacto con Issac | Por definir | Por definir | Dar acceso a su contenido opcional |
| Espacio de enfrentamiento final | Se propone un atrio con foso de cristal violeta | Columnas; el resto, por definir | Permitir combatir al Ascendido |

## Modularidad

¿Qué elementos pueden reutilizarse?

El kit de CERBERUS se arma sobre una rejilla de 2 m y se reutiliza en todo el complejo. Está a escala humana: 1 unidad de Blender equivale a 1 unidad de Unity y a 1 m, la misma escala de Eco-10, que mide 1.85 m. Las medidas están en metros (ancho × fondo × alto):

| Pieza | Medidas | Triángulos |
|---|---|---|
| Piso | 2 × 2 × 0.1 | 12 |
| Muro | 2 × 0.2 × 3 | 12 |
| Muro con puerta | 2 × 0.26 × 3 y 4 × 0.26 × 3 | 72 |
| Hoja de puerta | 1.6 × 0.11 × 2.4 y 1.6 × 0.11 × 2.8 | 36 |
| Columna | 0.6 × 0.6 × 3 | 48 |
| Poste de esquina | 0.34 × 0.34 × 3 | 24 |
| Caja | 0.5 y 1 de lado | 156 |
| Panel de pared | 0.8 × 0.17 × 1 | 48 |
| Tubería recta | 2 × 0.28 × 0.28 | 84 |
| Codo de tubería | 0.4 × 0.4 × 0.2 | 76 |
| Señal de sector | 1 × 0.035 × 0.4 | 48 |
| Marcas de piso | Flecha 0.8 × 0.44, peligro 2 × 0.3 y línea 2 × 0.1 | 2 a 21 |
| Generador | Base de 1.6 × 2.56 × 1.56 y mástil de 2.72 de alto | 742 operativo, 706 apagado y 550 destruido |
| Zona de interacción del generador | 1.2 × 1 × 1.8 | Sin modelo visible |

Piezas del kit, agrupadas como en `AfterLight_Kit_CERBERUS.blend`:

- **Estructura:** ![[Kit - Estructura.png|380]]
- **Utilería:** ![[Kit - Utilería.png|380]]
- **Generador:** ![[Kit - Generador.png|380]]
- **Laboratorio:** ![[Kit - Laboratorio.png|380]]
- **Cristales:** ![[Kit - Cristales.png|380]]
- **Centro:** ![[Kit - Centro.png|380]]
- **Sectores:** ![[Kit - Sectores.png|380]]
- **Rastros:** ![[Kit - Rastros.png|380]]

## Iluminación

Describe iluminación global, fuentes de luz y cambios durante el juego.

La luz global es casi nula: el prototipo usa una luz ambiental plana `#14141A`, sin cielo ni niebla, para que el espacio dependa de las fuentes localizadas que describe [[01 - Dirección de Arte]].

Las fuentes de luz son la linterna, con 8 m de alcance y 60° de apertura, y los generadores operativos, con 9 m de alcance. Los cristales de los Vimers emiten un brillo violeta que no debilita. Se propone que las luces rojas de emergencia marquen solo las esquinas de los pasillos.

La iluminación cambia con los generadores: un generador averiado o destruido deja de iluminar su zona. Cada generador operativo suma 1 m de alcance y 5° de apertura a la linterna.

## Efectos visuales

- Partículas: esporas en el ambiente, muerte de enemigos y recogida de cristales.
- Clima: no aplica; el nivel transcurre en interiores.
- Humo: en lo alto del generador dañado; por diseñar.
- Fuego: explosión del generador al destruirse; por diseñar.
- Agua: no aplica.
- Magia / energía: resplandor de los cristales y del halo del Ascendido; la recarga junto al generador está por diseñar.
- Impactos: fogonazo del arma, impacto de bala y chispas del generador.

## Recursos requeridos

Lista los modelos, sprites, texturas, materiales y efectos necesarios.

- **Modelos:** Kit de CERBERUS y generador en sus tres estados, listos. Faltan los elementos de los laboratorios, el punto de contacto con Issac y el espacio final.
- **Sprites:** No aplica; los escenarios son modelos 3D.
- **Texturas:** Cada pieza del kit tiene su propia textura horneada, de 128 a 1024 px; el generador usa un atlas de 1024 px.
- **Materiales:** Usan los colores de [[01 - Dirección de Arte]], salvo tres tonos oscuros de apoyo: `#2B3036`, `#0E1013` y `#1E2626`.
- **Efectos:** Dos efectos de Visual Effect Graph, el fogonazo y el impacto, y el efecto de cámara pixelada. Faltan el humo, la explosión, la recarga y el filtro VHS.

## Decisiones pendientes

- El generador del kit ocupa 1.6 × 2.56 m y el plano propuesto le reserva 2 × 2 m.
- Unificar la resolución de texturas: el kit usa de 128 a 1024 px por pieza, el soldado 1024 px y el arma 256 px. La regla 1 de [[01 - Dirección de Arte]] pide un mismo criterio.


> **Navegación:** [[00 - Índice]] · ← [[02 - Personajes y Animación]] · [[04 - Interfaz Visual]] →
