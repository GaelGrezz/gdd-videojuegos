 # Personajes y Animación

## Descripción de la sección

Documenta cómo deben verse y comportarse visualmente los personajes.

## Requisitos por personaje

| Personaje | Modelo/Sprite | Animaciones | VFX | Estado |
|---|---|---|---|---|
| Eco-10 | Modelo 3D low poly de 2672 triángulos con rig humanoide de 23 huesos. Lleva el arma CERBERUS, de 620 triángulos | Reposo, caminar, carrera, disparo, recarga y recibir daño | Fogonazo e impacto de bala | En progreso |
| Cáscara | Modelo 3D low poly de 868 triángulos con rig humanoide de 41 huesos, 18 de ellos en los dedos. Lleva 37 cristales de 724 triángulos en total, en el brazo, el hombro, el pecho, la cabeza y la pierna derechos | Reposo, caminar, persecución, preparar el ataque, atacar, recuperarse, recibir daño y muerte | Destello blanco al recibir daño, brillo que late mientras la linterna la debilita y muerte | En progreso |
| Quimera | Modelo 3D low poly con un núcleo de cristal, un ojo frontal y cuatro extremidades de 298 triángulos cada una, que reutilizan el rig de 41 huesos de la Cáscara. Lleva 120 cristales de 3600 triángulos en total y un ojo de 224 | Reposo, caminar, preparar el ataque, atacar, recuperarse, recibir daño y muerte | Destello blanco al recibir daño, brillo que late mientras la linterna la debilita y muerte | En progreso |
| Ascendido | Primitivas en el prototipo: cuerpo, cuatro brazos suspendidos y halo de prismas; modelo por diseñar | Por definir. El prototipo mueve el cuerpo y los brazos por código: aparición desde el suelo, golpe dirigido, barrido, impacto convergente y absorción por el halo | Señales rojas en el suelo antes de cada ataque, destello blanco al recibir daño y brillo de los ojos y el halo que late mientras la linterna lo debilita | En progreso |

## Animaciones

### Movimiento

- Idle: `Idle_Aim` de Eco-10, 151 frames, con el arma al hombro.
- Caminar: `Walk_Rifle` de Eco-10, 33 frames.
- Correr: `Run_Rifle_v2` de Eco-10, 21 frames, con el arma cruzada sobre el cuerpo.
- Idle de la Cáscara: `Cascara_Idle`, 91 frames. Encorvada, con la cabeza ladeada hacia los cristales, jadea y da un tirón de cabeza.
- Caminar de la Cáscara: `Cascara_Walk`, 33 frames, a 1 m/s. Arrastra la pierna derecha; se usa al arrancar y al frenar.
- Persecución de la Cáscara: `Cascara_Chase`, 21 frames, a 3.2 m/s, con el torso inclinado y los brazos sueltos.
- Idle de la Quimera: `Quimera_Idle`, 97 frames. El núcleo respira y se balancea, el ojo mira a los lados y recoloca dos extremidades.
- Caminar de la Quimera: `Quimera_Walk`, 41 frames a 24 fps, hecha con el modelo. Avanza unos 0.26 m/s y en el juego se acelera hasta su velocidad de 1 m/s.
- Saltar: no aplica; el juego no tiene salto.
- Caer: no aplica.

![[Eco-10 - Reposo.mp4|380]]
![[Eco-10 - Caminar.mp4|380]]
![[Eco-10 - Correr.mp4|380]]
![[Cáscara - Reposo.mp4|380]]
![[Cáscara - Caminar.mp4|380]]
![[Cáscara - Persecución.mp4|380]]
![[Quimera - Reposo.mp4|380]]
![[Quimera - Caminar.mp4|380]]

### Interacción

- Reparar generadores: por definir.
- Recuperar registros: por definir.

### Combate

- Disparar: `Shoot_Rifle` de Eco-10, 11 frames, un retroceso por bala.
- Recargar: `Reload_Rifle` de Eco-10, 55 frames.
- Preparar el ataque, atacar y recuperarse de la Cáscara: `Cascara_Attack`, 52 frames, dividida en preparar (0.6 s), atacar (0.2 s) y recuperarse (0.9 s), los tiempos de [[03 - Enemigos y NPC]]. Levanta el brazo de los cristales, tiembla y lanza un zarpazo en diagonal; después queda encorvada y expuesta.
- Preparar el ataque, atacar y recuperarse de la Quimera: `Quimera_Attack`, 60 frames, dividida en preparar (0.8 s), atacar (0.2 s) y recuperarse (1 s). Se encabrita, levanta la extremidad delantera derecha por encima del núcleo y la clava delante; la deja clavada un momento y vuelve.
- Evasión lateral de la Quimera: por definir. El prototipo la desplaza 3 m en 0.35 s sin una animación propia.
- Golpe dirigido, barrido e impacto convergente del Ascendido: por definir.

![[Eco-10 - Disparar.mp4|380]]
![[Eco-10 - Recargar.mp4|380]]
![[Cáscara - Ataque.mp4|380]]
![[Quimera - Ataque.mp4|380]]

### Daño

- Recibir daño: `Hit_Rifle` de Eco-10, 17 frames, con cada golpe que no lo derrota. El torso se echa hacia atrás, el arma se sale de la mira y vuelve a la pose de disparo; no interrumpe la recarga.
- Recibir daño de la Cáscara: `Cascara_Hit`, 17 frames. Sacudida del torso y la cabeza que se suma a la animación en curso, también al correr.
- Recibir daño de la Quimera: `Quimera_Hit`, 17 frames. Sacudida del núcleo y del ojo que se suma a la animación en curso.

![[Eco-10 - Recibir daño.mp4|380]]
![[Cáscara - Recibir daño.mp4|380]]
![[Quimera - Recibir daño.mp4|380]]

### Muerte / derrota

- Eco-10: la derrota abre directamente Game Over, según [[02 - UI y Menús]].
- Cáscara: `Cascara_Death`, 48 frames. Se dobla, cae de rodillas y queda de bruces; el último frame se mantiene hasta que desaparece el cuerpo.
- Quimera: `Quimera_Death`, 54 frames. Se sacude, las extremidades ceden y se abren y el núcleo cae al suelo; el último frame se mantiene hasta que desaparece el cuerpo.
- Ascendido: el cuerpo y los brazos son absorbidos por el halo; por definir.

![[Cáscara - Muerte.mp4|380]]
![[Quimera - Muerte.mp4|380]]

## Convenciones

Define nombres de archivos, tamaños, esqueletos, rigging, frames o formatos cuando sea necesario.

- **Formato:** Modelos FBX exportados desde Blender, a 30 frames por segundo.
- **Esqueleto:** Rig humanoide compatible con Unity.
- **Animaciones:** Una toma por acción, cada una en su propio FBX, con nombres como `Idle_Aim`, `Run_Rifle_v2` y `Cascara_Attack`.
- **Texturas:** Soldado a 1024 px. Arma a 256 px en color, con filtrado Point. Cáscara a 682 px en color y emisión, y a 2048 px en normal, metálico y rugosidad; sus cristales a 341 px y 1024 px. La Quimera usa las texturas de la Cáscara en las extremidades; sus cristales y su ojo van a 682 px en color y emisión y a 2048 px en normal, metálico y rugosidad.
- **Tamaños:** Eco-10 mide 1.85 m en Unity y 4.31 unidades en Blender. El arma mide 1.39 unidades de largo. La Cáscara mide 1.83 m en Unity y 4.27 unidades en Blender, a la misma escala que Eco-10. La Quimera mide 1.82 m de alto, 2.26 m de largo y 1.84 m de ancho en Unity, 4.24 unidades de alto en Blender, a la misma escala. El tamaño del Ascendido está por definir; se proponen 3.2 m de alto sin el halo, los del prototipo.


> **Navegación:** [[00 - Índice]] · ← [[01 - Dirección de Arte]] · [[03 - Entornos]] →
