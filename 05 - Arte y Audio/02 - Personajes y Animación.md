# Personajes y Animación

## Descripción de la sección

Documenta cómo deben verse y comportarse visualmente los personajes.

## Requisitos por personaje

| Personaje | Modelo/Sprite | Animaciones | VFX | Estado |
|---|---|---|---|---|
| Eco-10 | Modelo 3D low poly de 2672 triángulos con rig humanoide de 23 huesos. Lleva el arma CERBERUS, de 620 triángulos | Reposo, caminar, carrera, disparo y recarga | Fogonazo e impacto de bala | En progreso |
| Cáscara | Primitivas en el prototipo; modelo por diseñar | Por definir | Muerte | Pendiente |
| Quimera | Primitivas en el prototipo; modelo por diseñar | Por definir | Muerte | Pendiente |
| Ascendido | Primitivas en el prototipo: cuerpo, cuatro brazos y halo; modelo por diseñar | Por definir | Por definir | Pendiente |

## Animaciones

### Movimiento

- Idle: `Idle_Rifle` de Eco-10, 91 frames.
- Caminar: `Walk_Rifle` de Eco-10, 33 frames.
- Correr: `Run_Rifle` de Eco-10, 25 frames.
- Saltar: no aplica; el juego no tiene salto.
- Caer: no aplica.

![[Eco-10 - Reposo.mp4|380]]
![[Eco-10 - Caminar.mp4|380]]
![[Eco-10 - Correr.mp4|380]]

### Interacción

- Abrir las puertas en el menú principal y en la entrada al complejo: por definir.
- Reparar generadores: por definir.
- Recuperar registros: por definir.

### Combate

- Disparar: `Shoot_Rifle` de Eco-10, 11 frames, un retroceso por bala.
- Recargar: `Reload_Rifle` de Eco-10, 55 frames.
- Preparar el ataque, atacar y recuperarse de la Cáscara y la Quimera: por definir.
- Evasión lateral de la Quimera: por definir.
- Golpe dirigido, barrido e impacto convergente del Ascendido: por definir.

![[Eco-10 - Disparar.mp4|380]]
![[Eco-10 - Recargar.mp4|380]]

### Daño

- Recibir daño: por definir.

### Muerte / derrota

- Eco-10: pantalla roja con siluetas negras según la causa, descrita en [[04 - Diálogos y Narrativa]]; por definir.
- Cáscara y Quimera: por definir.
- Ascendido: el cuerpo y los brazos son absorbidos por el halo; por definir.

## Convenciones

Define nombres de archivos, tamaños, esqueletos, rigging, frames o formatos cuando sea necesario.

- **Formato:** Modelos FBX exportados desde Blender, a 30 frames por segundo.
- **Esqueleto:** Rig humanoide compatible con Unity.
- **Animaciones:** Una toma por acción, con nombres como `Idle_Rifle` y `Run_Rifle`.
- **Texturas:** Soldado a 1024 px. Arma a 256 px en color, con filtrado Point.
- **Tamaños:** Eco-10 mide 1.85 m en Unity y 4.31 unidades en Blender. El arma mide 1.39 unidades de largo. Los tamaños de la Cáscara, la Quimera y el Ascendido están por definir.

## Decisiones pendientes

- El modelo de Unity usa `Idle_Aim`, de 151 frames, y `Run_Rifle_v2`, de 21 frames; esta nota dice `Idle_Rifle`, de 91 frames, y `Run_Rifle`, de 25 frames. Los videos de reposo y carrera muestran las tomas de Unity.


> **Navegación:** [[00 - Índice]] · ← [[01 - Dirección de Arte]] · [[03 - Entornos]] →
