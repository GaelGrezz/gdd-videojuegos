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
└── GameManager / Mediator
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

# Componentes principales

|Componente|Responsabilidad|Dependencias|
|---|---|---|
|**GameManager**|Controla el estado general de la partida: inicio, pausa, victoria, derrota y finalización.|GameMediator, sistemas principales|
|**GameMediator**|Coordina la comunicación entre sistemas globales sin obligarlos a conocerse directamente.|GameManager, DirectorIA, Generadores, Progresión|
|**PlayerController**|Gestiona movimiento, orientación e interacción básica del jugador.|Input System, Rigidbody|
|**PlayerCombat**|Gestiona disparos, armas, cadencia y acciones ofensivas.|WeaponSystem, Input System|
|**FlashlightSystem**|Controla batería, alcance, intensidad y efectos de la linterna sobre enemigos.|PlayerStats, enemigos afectados|
|**HealthSystem**|Gestiona vida, daño, curación y muerte de entidades.|DamageSystem|
|**WeaponSystem**|Administra las armas equipadas y sus comportamientos.|WeaponData, ProjectileFactory|
|**EnemyController**|Coordina el comportamiento general de cada enemigo.|State Machine, Strategy|
|**EnemyStateMachine**|Controla estados como persecución, ataque, evasión o muerte.|EnemyController|
|**DirectorIA**|Determina cuándo, dónde y qué enemigos deben aparecer durante la partida.|Sistema de Tickets, EnemyFactory|
|**EnemyFactory**|Crea enemigos a partir de configuraciones definidas.|EnemyData, prefabs|
|**GeneratorSystem**|Controla estado, reparación, daño y funcionamiento de los generadores.|GameMediator|
|**UpgradeSystem**|Gestiona selección y aplicación de mejoras durante la partida.|UpgradeData, PlayerStats|
|**ProgressionSystem**|Controla experiencia, cristales, nivel y selección de mejoras.|UpgradeSystem|
|**SaveSystem**|Guarda y recupera configuraciones y progreso persistente.|Datos serializables|
|**UIManager**|Actualiza HUD, menús y pantallas según el estado del juego.|Eventos de gameplay|
|**AudioManager**|Reproduce música, ambientes y efectos de sonido.|Eventos del juego|
|**VFXManager**|Gestiona efectos visuales reutilizables como impactos, cristales y partículas.|Eventos de combate|

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
# GameManager

`GameManager` mantiene el estado global de la partida.

Estados previstos:

```text
MainMenu
Loading
Playing
Paused
Victory
Defeat
GameOver
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
│ Idle                │
│ Chase               │
│ Attack              │
│ Evade               │
│ Stunned             │
│ Dead                │
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

Cada brazo puede:

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

# Estructura propuesta del código

```text
Assets/
└── Code/
    ├── Core/
    │   ├── GameManager
    │   ├── GameMediator
    │   └── Interfaces
    │
    ├── Player/
    │   ├── PlayerController
    │   ├── PlayerCombat
    │   ├── PlayerStats
    │   └── Flashlight
    │
    ├── Combat/
    │   ├── Weapons
    │   ├── Projectiles
    │   ├── Damage
    │   └── Health
    │
    ├── Enemies/
    │   ├── AI
    │   ├── States
    │   ├── Strategies
    │   ├── Factory
    │   └── Bosses
    │
    ├── Systems/
    │   ├── Director
    │   ├── Generators
    │   ├── Progression
    │   └── Upgrades
    │
    ├── Data/
    │   ├── PlayerData
    │   ├── EnemyData
    │   ├── WeaponData
    │   └── UpgradeData
    │
    ├── UI/
    ├── Audio/
    ├── VFX/
    └── Save/
```

Esta estructura funciona como referencia inicial y puede cambiar conforme aumente la complejidad del proyecto. El objetivo no es mantener una jerarquía rígida, sino evitar que código de responsabilidades diferentes termine mezclado.

> **Navegación:** [[00 - Índice]] · ← [[04 - Guardado y Configuración]] · [[02 - Motor y Herramientas]] →
