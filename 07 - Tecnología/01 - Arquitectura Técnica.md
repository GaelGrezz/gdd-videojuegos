# Arquitectura Técnica

## Descripción de la sección

Explica cómo está construido técnicamente el videojuego y cómo se comunican sus componentes.

## Arquitectura general

```text
Entrada del jugador
        ↓
Controladores
        ↓
Lógica de gameplay
        ↓
Sistemas principales
        ↓
Datos / Configuración
        ↓
Presentación
```

De forma más específica:

```text
Input System
    ↓
PlayerController
    ↓
─────────────────────────────────
Gameplay
├── Movimiento
├── Combate
├── Linterna
├── Interacción
└── Vida / Recursos
    ↓
─────────────────────────────────
Sistemas
├── Director de IA
├── Enemigos
├── Generadores
├── Mejoras
├── Progresión
└── Estado de la partida (Juego)
    ↓
─────────────────────────────────
Datos
├── ScriptableObjects
├── Configuración
├── Estadísticas
└── Guardado
    ↓
─────────────────────────────────
Presentación
├── UI / HUD
├── VFX
├── Audio
└── Animaciones
```


---

## Componentes implementados en Unity

|Componente|Responsabilidad|Dependencias|
|---|---|---|
|**Juego**|Mantiene el estado global de la partida: pausa, selección de mejora, carga y fin. Detiene el tiempo cuando corresponde.|PantallaCarga, MenuPausa, PantallaMejoras, FinPartida|
|**InputHandler**|Lee mover, disparar, recargar y caminar del asset de Input Actions.|Input System, PlayerController, PlayerCombat|
|**PlayerController**|Movimiento, carrera y caminata, y orientación hacia el cursor.|CharacterController, InputHandler|
|**PlayerCombat**|Disparo, cadencia, cargador y recarga del arma inicial.|Projectile, InputHandler|
|**Projectile**|Bala que avanza, daña a un `IDamageable` y crea el efecto de impacto.|IDamageable, VFX|
|**Health**|Vida, daño, reducción de daño, invulnerabilidad y muerte de cualquier entidad.|IDamageable|
|**PlayerHealth**|Regeneración de la salud del soldado y derrota *Operativo caído*.|Health, FinPartida|
|**BatterySystem**|Carga, consumo y periodo de tolerancia de la batería; derrota *Sin luz*.|FlashlightSystem, Generador, FinPartida|
|**FlashlightSystem**|Cono de luz, enemigos iluminados, daño extra y bonificación de los generadores operativos.|BatterySystem, Generador|
|**Cascara**|IA de la Cáscara: estados, persecución por NavMesh, golpe y muerte.|NavMesh, Health, ProgressionSystem|
|**DirectorIA**|Tickets, catálogo de enemigos, grupos y puntos de aparición.|Cascara, Generador|
|**Generador**|Reparación, integridad, invulnerabilidad, recarga de batería y estado del generador.|InteraccionGenerador, GeneratorVisuals, HUD|
|**InteraccionGenerador**|Repara el generador cercano mientras se mantiene E.|Generador|
|**ProgressionSystem**|Cristales, nivel y racha; abre Elige una mejora al subir de nivel.|Cristal, UpgradeSystem|
|**UpgradeSystem**|Ofrece tres cartas y aplica sus efectos.|UpgradeData, sistemas del jugador|
|**Configuracion**|Ajustes de Opciones guardados en `PlayerPrefs`.|PantallaOpciones|
|**HUD y RetroalimentacionHUD**|Vida, batería, generadores, nivel, cristales, racha, avisos y efectos de daño.|Sistemas del jugador|
|**SoldierAnimator**|Animaciones de Eco-10 según la velocidad, el disparo, la recarga y el daño.|Animator|
|**CamaraSeguimiento y OclusionCamara**|Siguen al soldado, adelantan el encuadre hacia el cursor y transparentan los obstáculos que lo ocultan.|PlayerController, cámara y geometría del nivel|
|**Quimera**|Extiende la IA de Cáscara con prioridad a generadores, zona de peligro y evasión lateral al recibir luz.|Cascara, Health, Generador, NavMesh|
|**RelojPartida, Ascendido y AscendidoBrazo**|El reloj crea al jefe a los 600 s y pausa al director. El jefe coordina sus brazos, ataques y derrota. Al finalizar el fundido, el reloj selecciona el resultado con la cadena de Issac.|DirectorIA, NavMesh, CadenaIssac, FinPartida|
|**Registro, InteraccionObjetos, CadenaIssac y TerminalIssac**|Gestionan los 28 registros, la interacción de recogida, las peticiones y la preparación de la copia en la terminal del Archivo.|Input System, Generador Norte, ComunicacionHUD|
|**ComunicacionHUD, JefeHUD y MejorasHUD**|Presentan mensajes encolados, información del jefe y estado de mejoras. Complementan el HUD principal.|HUD, RelojPartida, ProgressionSystem, UpgradeSystem|
|**MenuPrincipal, PantallaCarga y FinPartida**|Navegan entre escenas, muestran el avance o error de carga y presentan Victoria o Game Over.|Juego, SceneManager, prefabs de interfaz|
|**MenuPausa, PantallaMejoras y DialogoConfirmacion**|Detienen la simulación en los menús que lo requieren y controlan la selección o confirmación.|Juego, Input System, UpgradeSystem|
|**PantallaOpciones y PantallaCreditos**|Abren paneles de configuración y créditos desde recursos de interfaz.|Configuracion, MenuPrincipal, MenuPausa|
|**Sonido y MusicaPartida**|Reproducen efectos y música de la partida con niveles de volumen independientes.|Configuracion, AudioSource, AudioListener|
|**PixeladoCamaraFeature**|Aplica pixelado al renderizado 3D antes del HUD en Overlay.|URP, PC_Renderer, shader de pixelado|

---

# Entrada

El proyecto utiliza el **Unity Input System**.

Las entradas del jugador deben interpretarse mediante acciones y no mediante comprobaciones directas distribuidas por todo el código.

Ejemplos:

```text
Move
Aim
Fire
Interact
Pause
```

La linterna no tiene una acción propia: permanece encendida y se orienta con `Aim`, igual que el arma.

El flujo esperado es:

```text
Input Action
    ↓
PlayerController
    ↓
Sistema correspondiente
```

Por ejemplo:

```text
Fire
 ↓
PlayerCombat
 ↓
WeaponSystem
 ↓
Weapon
 ↓
ProjectileFactory
 ↓
Projectile
```

Esto permite cambiar controles o dispositivos sin modificar la lógica de las armas.

---
## Patrones de arquitectura considerados

Las secciones sobre `GameManager`, `GameMediator`, Factory, Builder, Composite, Decorator y Dirty Flag describen alternativas de arquitectura. La partida actual usa `Juego`, componentes de Unity, referencias directas y eventos. La tabla anterior refleja la implementación revisada.

# GameManager

`GameManager` mantiene el estado global de la partida.

Estados previstos:

```text
MainMenu
Loading
Playing
UpgradeSelection
Paused
Victory
Defeat
GameOver
Credits
```

Sus responsabilidades incluyen:

- iniciar una partida;
- pausar y reanudar;
- detectar condiciones de victoria;
- detectar condiciones de derrota;
- terminar la partida;
- coordinar cambios importantes de estado.

No debe encargarse directamente de controlar enemigos, armas, generadores o interfaz.

Su función es administrar el **estado global**, no convertirse en una clase que controle todo el juego.

---

# GameMediator

El `GameMediator` coordina sistemas que necesitan reaccionar entre sí.

Ejemplo:

```text
Generador reparado
       ↓
GameMediator
   ↙              ↘
FlashlightSystem   UI
   ↓
Habilita la recarga de batería
```

Otro ejemplo:

```text
Jugador muere
     ↓
GameMediator
     ↓
GameManager
     ↓
Defeat
     ↓
UI / Audio / Gameplay
```

Esto evita dependencias como:

```text
Generator
 → GameManager
 → UIManager
 → EnemySpawner
 → AudioManager
```


---
# Sistema de jugador

El jugador debe dividirse en componentes pequeños con responsabilidades específicas.

```text
Player
├── PlayerController
├── PlayerCombat
├── HealthSystem
├── FlashlightSystem
├── PlayerStats
├── InteractionSystem
└── WeaponSystem
```

Esto permite modificar un sistema sin afectar directamente los demás.

Por ejemplo, `PlayerController` no necesita saber cómo funciona el arma y `PlayerCombat` no necesita controlar el movimiento.

---

# Sistema de enemigos

Los enemigos utilizan diferentes patrones dependiendo de la responsabilidad.

```text
EnemyController
      ↓
State Machine
      ↓
┌─────────────────────┐
│ AdquirirObjetivo    │
│ Perseguir           │
│ PrepararAtaque      │
│ Atacar              │
│ Recuperarse         │
│ Buscar              │
│ Morir               │
└─────────────────────┘
```

## State

El patrón **State** controla el comportamiento actual del enemigo.

Ejemplo:

```text
Chase
 ↓
Detecta luz
 ↓
Evade
 ↓
Cooldown terminado
 ↓
Chase
```

Esto permite crear enemigos con comportamientos complejos sin llenar una única clase de condiciones.

---

## Strategy

El patrón **Strategy** se utiliza cuando diferentes enemigos pueden compartir una acción pero ejecutarla de distintas maneras.

Ejemplo:

```text
IAttackStrategy
├── MeleeAttack
├── RangedAttack
├── ChargeAttack
└── AreaAttack
```

También puede utilizarse para movimiento:

```text
IMovementStrategy
├── DirectChase
├── DashMovement
├── OrbitMovement
└── KeepDistance
```

---

# Director de IA

El Director de IA controla la presión general sobre el jugador.
No controla individualmente a cada enemigo.

Determina:

- cantidad de enemigos;
- tipo de enemigo;
- frecuencia de aparición;
- zonas disponibles;
- intensidad de las oleadas;
- enemigos especiales;
- escalado según tiempo o progreso.

Utiliza un **Sistema de Tickets**.

Ejemplo:

```text
Tickets disponibles: 10

Cáscara        = 1
Quimera        = 3
```

El Director puede construir una oleada como:

```text
4 Cáscaras     = 4
2 Quimeras     = 6
-----------------
Total          = 10
```

La cantidad máxima de tickets aumenta progresivamente durante la partida.

---

# Factory y Builder

## Factory

Las entidades que pueden existir en múltiples variantes deben crearse mediante fábricas cuando resulte conveniente.

Ejemplo:

```text
EnemyFactory
    ↓
EnemyData
    ↓
Prefab
    ↓
Enemy
```

Esto permite solicitar:

```text
Crear Cáscara
Crear Quimera
Crear Ascendido
```

sin que el sistema que realiza la solicitud conozca los detalles de construcción.

---

## Builder

El patrón **Builder** puede utilizarse para construir variantes más complejas.

Ejemplo:

```text
EnemyBuilder

Base:
Cáscara

+
Vida aumentada

+
Velocidad modificada

+
Estado élite

+
Efecto especial

=

Cáscara Élite
```

La Cáscara Élite es un ejemplo hipotético; no forma parte del diseño actual.

Debe utilizarse únicamente cuando la creación de una entidad requiera múltiples configuraciones.

---

# Composite

El patrón **Composite** puede utilizarse para enemigos formados por varias entidades independientes.

El principal caso previsto es el **Ascendido**.

```text
Ascendido
├── Cuerpo
├── Brazo 01
├── Brazo 02
├── Brazo 03
└── Brazo 04
```

Cada brazo podría, según se defina en [[03 - Enemigos y NPC]]:

- recibir daño;
    
- ejecutar ataques;
    
- ser destruido;
    
- tener comportamiento propio.
    

El Ascendido continúa tratándose como una sola entidad lógica.

---

# Sistema de mejoras

Las mejoras deben estar separadas de la lógica específica del jugador.

```text
UpgradeData
     ↓
UpgradeSystem
     ↓
UpgradeEffect
     ↓
Objetivo
```

Ejemplo:

```text
Carta:
"Batería extendida"

Efecto:
+20 % capacidad

Objetivo:
FlashlightSystem
```

Esto permite añadir nuevas cartas sin modificar directamente el código central del jugador.

---

# Decorator

Los efectos temporales o modificaciones acumulables pueden modelarse conceptualmente mediante **Decorator**.

Ejemplo:

```text
Enemigo base
    ↓
Debilitado por luz
    ↓
Marcado
    ↓
Vulnerable
```

También puede utilizarse para las modificaciones de la linterna:

```text
Linterna base
    ↓
Mayor alcance
    ↓
Mayor debilidad
    ↓
Daño adicional
```

No necesariamente todos estos efectos requieren implementar literalmente una clase Decorator. El patrón se utiliza cuando ayude a mantener efectos combinables y desacoplados.

---

# Datos y configuración

Las estadísticas que el equipo necesite modificar frecuentemente deben mantenerse fuera de la lógica siempre que sea posible.

Se utilizarán principalmente `ScriptableObject`.

Ejemplo:

```text
EnemyData
├── Health
├── Damage
├── Speed
├── TicketCost
├── AttackRange
└── Prefab
```

Otros datos previstos:

```text
PlayerData
WeaponData
EnemyData
UpgradeData
GeneratorData
WaveData
AudioData
```

Esto permite que valores de balance puedan modificarse desde Unity sin cambiar código.

---

# Persistencia

El `SaveSystem` será responsable únicamente de datos que deban existir entre ejecuciones.

Ejemplos:

- configuración gráfica;
    
- volumen;
    
- controles;
    
    
- opciones de accesibilidad.
    
    

Los datos temporales de una partida permanecen en memoria y no necesariamente se almacenan.

---

# Presentación

Los sistemas de presentación reaccionan al estado del gameplay.

```text
Gameplay Event
      ↓
 ┌────┼────┐
 ↓    ↓    ↓
UI   VFX  Audio
```

Ejemplo:

```text
EnemyDamaged
   ↓
├── VFX de impacto
├── SFX de impacto
└── Indicador visual
```

La lógica de daño no debe depender directamente de cómo se representa visual o auditivamente.

---

# Comunicación

Los sistemas pueden comunicarse mediante cuatro mecanismos principales.

## 1. Referencias directas

Se utilizan cuando existe una relación clara de propiedad.

Ejemplo:

```text
Player
 ↓
PlayerCombat
 ↓
WeaponSystem
```

Son apropiadas para componentes estrechamente relacionados.

---

## 2. Interfaces

Se utilizan cuando diferentes objetos pueden ofrecer el mismo comportamiento.

Ejemplo:

```csharp
public interface IDamageable
{
    void TakeDamage(float damage);
}
```

Puede implementarlo:

```text
Player
Enemy
Generator
Objeto destructible
```

El proyectil no necesita conocer qué tipo de objeto golpeó.

Solo necesita comprobar si implementa `IDamageable`.

---

## 3. Eventos

Se utilizan para informar que ocurrió algo sin conocer quién reaccionará.

Ejemplos:

```text
OnPlayerDamaged
OnPlayerDeath
OnEnemyKilled
OnGeneratorRepaired
OnLevelUp
OnUpgradeSelected
```

Esto resulta especialmente útil para:

- UI;
    
- audio;
    
- VFX;
    
- estadísticas;
    
- progresión.
    

---

## 4. Mediator

Se utiliza cuando un evento necesita provocar cambios coordinados en varios sistemas.

Ejemplo:

```text
Generador destruido
       ↓
GameMediator
       ↓
├── FlashlightSystem desactiva la recarga de ese generador
├── UI muestra alerta
└── Audio cambia
```

---

# Dirty Flag

El patrón **Dirty Flag** se utilizará cuando un dato costoso de recalcular solamente necesite actualizarse después de un cambio.

Ejemplo:

```text
Estadísticas base
      +
Mejoras
      +
Efectos temporales
      ↓
Estadísticas finales
```

Cuando una mejora cambia:

```text
statsDirty = true
```

Las estadísticas se recalculan únicamente cuando vuelvan a necesitarse.

Esto evita realizar cálculos innecesarios cada frame.

---

# Principios técnicos

- Mantener bajo acoplamiento cuando sea razonable.
    
- Cada clase debe tener una responsabilidad principal claramente identificable.
    
- Favorecer composición sobre herencia excesiva.
    
- Separar datos de configuración de la lógica.
    
- Utilizar `ScriptableObject` para estadísticas y configuraciones reutilizables.
    
- Evitar referencias globales innecesarias.
    
- Utilizar eventos para comunicar cambios de estado.
    
- Utilizar interfaces para comportamientos compartidos.
    
- Evitar llamadas costosas dentro de `Update()` cuando puedan ejecutarse mediante eventos.
    
- No utilizar `GameManager` como contenedor de toda la lógica.
    
- Evitar crear patrones de diseño cuando una solución simple sea suficiente.
    
- Diseñar sistemas pensando en que nuevos enemigos, armas y mejoras puedan añadirse con cambios mínimos.
    
- Separar gameplay y presentación siempre que sea razonable.
    
- Mantener nombres consistentes entre documentación, código y Unity.
    

---

# Estructura del código

```text
Assets/
└── Code/
    ├── Scripts/
    │   ├── Combat/       Health, IDamageable, Projectile
    │   ├── Core/         Juego, Configuracion
    │   ├── Enemies/      Cascara, DirectorIA
    │   ├── Level/        Generador, GeneratorVisuals
    │   ├── Player/       PlayerController, PlayerCombat, PlayerHealth, BatterySystem,
    │   │                 FlashlightSystem, InteraccionGenerador, InputHandler,
    │   │                 SoldierAnimator, CamaraSeguimiento
    │   ├── Progression/  Cristal, ProgressionSystem
    │   ├── Render/       PixeladoCamaraFeature
    │   ├── UI/           HUD, menús y pantallas
    │   └── Upgrades/     UpgradeData, UpgradeSystem
    ├── Shaders/          Pixelado
    └── Editor/           CerberusKitImporter
```

La estructura puede cambiar conforme aumente la complejidad del proyecto. El objetivo no es mantener una jerarquía rígida, sino evitar que código de responsabilidades diferentes termine mezclado.

## Decisiones pendientes

- Unity no usa `GameManager`, `GameMediator`, Factory, Builder, Composite ni Decorator: el estado de la partida lo lleva `Juego` y los sistemas se comunican con referencias directas y eventos. Falta decidir si esos patrones siguen siendo la meta o se quitan de esta nota.


> **Navegación:** [[00 - Índice]] · ← [[04 - Guardado y Configuración]] · [[02 - Motor y Herramientas]] →
