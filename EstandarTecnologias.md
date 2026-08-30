# Estándar de codificación

## Desarrollo de videojuegos en C#

**Institución:** Universidad Veracruzana
**Asignatura:** Tecnologías para la Construcción de Software  
**Integrantes:**  
- Carreto Barrientos Samuel
- Juarez Reyes Denisse Yamileth

**Fecha:** 23 de agosto de 2026

<div style="page-break-after: always;"></div>

## Índice

1. [Introducción](#1-introducción)
2. [Organización del proyecto](#2-organización-del-proyecto)
3. [Control de versiones](#3-control-de-versiones)
4. [Reglas de nombrado](#4-reglas-de-nombrado)
5. [Estilo de código](#5-estilo-de-código)
6. [Estructuras de control](#6-estructuras-de-control)
7. [Manejo de errores y excepciones](#7-manejo-de-errores-y-excepciones)
8. [Complejidad](#8-complejidad)
9. [Prácticas específicas de C#](#9-prácticas-específicas-de-c)
10. [Comentarios y documentación](#10-comentarios-y-documentación)
11. [Manejo de logs y categorización de errores](#11-manejo-de-logs-y-categorización-de-errores)
12. [Gestión de estados, pantallas y UI](#12-gestión-de-estados-pantallas-y-ui)
13. [Validación de entradas y seguridad](#13-validación-de-entradas-y-seguridad)
14. [Pruebas unitarias](#14-pruebas-unitarias)
15. [Dependencias externas](#15-dependencias-externas)
16. [Comunicación en red y operaciones asíncronas](#16-comunicación-en-red-y-operaciones-asíncronas)
17. [Declaración de uso de inteligencia artificial](#17-declaración-de-uso-de-inteligencia-artificial)
18. [Referencias](#18-referencias)

<div style="page-break-after: always;"></div>

## 1. Introducción

En este documento se definen las reglas a seguir para el desarrollo de nuestro proyecto de videojuego, tomando como base las convenciones oficiales “Microsoft C# Coding Conventions” que aseguran consistencia en el código, con el fin de que sea fácil de leer, entender y de mantener para cualquier miembro del equipo, además de unificar el formato para evitar problemas. Este estándar además de cubrir que el código se vea estético, sino también reglas de estructuras  que nos permitirán integrar las mecánicas en un producto final estable y unificado (Microsoft, 2025d; Martin, 2008).

### 1.1 Problemática

El desarrollo de un videojuego en un entorno escolar empleando buenas prácticas, así como también se busca que sea multijugador, empleando conocimientos de cursos anteriores, siendo conocimiento acumulativo.

### 1.2 Propósito

Se busca garantizar que el desarrollo del videojuego cumpla con los pilares de calidad necesarios para un producto final estable (Martin, 2008; McConnell, 2004):
- `Mantenibilidad`: asegurar que la arquitectura sea legible, escalable y comprensible para cualquier desarrollador del equipo, preservando su integridad técnica a largo plazo.
- `Detección temprana de errores`: facilitar la identificación de inconsistencias o desviaciones del estándar durante las revisiones de código, mitigando riesgos antes de las fases de entrega.
- `Productividad`: optimizar el flujo de trabajo al unificar criterios de formato, permitiendo que el equipo priorice la resolución de mecánicas y lógica de diseño sobre debates estéticos.
- `Rendimiento consistente`: garantizar que las convenciones de estilo no comprometan la eficiencia del ciclo de ejecución, especialmente en procesos críticos que impactan los cuadros por segundo.


### 1.3 Idioma del código

El código fuente se escribirá en inglés. Esta regla incluye los nombres de clases, métodos, variables, parámetros, constantes, comentarios y pruebas. También se escribirán en inglés los identificadores de la base de datos, incluidos los nombres de tablas, columnas, vistas, índices, restricciones y procedimientos almacenados. Los textos visibles para el usuario podrán escribirse en español según los requisitos del producto (Microsoft, 2026b).

Los identificadores deberán ser comprensibles y consistentes en todo el sistema. El uso del inglés es una decisión del equipo que evita mezclar idiomas entre el código, las pruebas y el esquema de datos; las convenciones oficiales de C# también recomiendan nombres claros y legibles para los identificadores (Microsoft, 2026b).

**Con estándar**

```csharp
private int _remainingLives;

public void LoseLife()
{
    _remainingLives--;
}
```

**Sin estándar**

```csharp
private int _vidasRestantes;

public void PerderVida()
{
    _vidasRestantes--;
}
```

## 2. Organización del proyecto

### 2.1 Stack tecnológico y entorno de desarrollo

### 2.2 Arquitectura general y patrones aplicables

### 2.3 Estructura de carpetas y namespaces

### 2.4 Separación entre lógica de dominio, infraestructura y presentación

## 3. Control de versiones

### 3.1 Commits

### 3.2 .gitignore y Git LFS (assets binarios)

## 4 Reglas de nombrado

Los identificadores deberán escribirse en inglés y describir claramente su propósito. Se priorizará la claridad sobre la brevedad y se evitarán abreviaturas, palabras reservadas y nombres de un solo carácter. Se permitirán identificadores de una letra únicamente en contadores de ciclos, excepciones capturadas y parámetros de eventos cuando su alcance sea menor o igual a tres líneas. También se permitirá el parámetro `e` cuando forme parte de la firma convencional de un manejador de eventos (Microsoft, 2026b).

No se utilizarán dos guiones bajos consecutivos, ya que estos nombres están reservados para identificadores generados por el compilador (Microsoft, 2026b).

C# utiliza principalmente:

- `PascalCase` para clases, estructuras, interfaces, métodos, propiedades, eventos, constantes y espacios de nombres.
- `camelCase` para variables locales y parámetros.
- `_camelCase` para todos los campos privados o internos, incluidos los campos estáticos.

Estas reglas corresponden a las convenciones oficiales para identificadores de C# (Microsoft, 2026b).

### 4.1 Variables y parámetros

Las variables locales y los parámetros deberán escribirse utilizando `camelCase`. Sus nombres deberán ser sustantivos o frases nominales que permitan comprender qué información almacenan (Microsoft, 2026b).

Se evitarán nombres de un solo carácter, excepto en contadores de ciclos simples como `i`, `j` o `k`, en excepciones capturadas como `ex` y en parámetros de eventos convencionales, siempre que su alcance sea menor o igual a tres líneas (Microsoft, 2026b).

**Con estándar**

```csharp
int remainingLives = 3;
```

**Sin estándar**

```csharp
int rl = 3;
```

Los parámetros también deberán tener nombres descriptivos (Microsoft, 2026b).

**Con estándar**

```csharp
public void AddExperience(int earnedExperience) 
{ 
}
```

**Sin estándar**

```csharp
public void AddExperience(int exp) 
{ 
}
```

### 4.2 Colecciones

Las variables y propiedades que representen colecciones deberán utilizar nombres en plural para indicar que contienen varios elementos (Microsoft, 2023a; Microsoft, 2026b).

**Con estándar**

```csharp
List<Enemy> activeEnemies = new();
```

**Sin estándar**

```csharp
List<Enemy> activeEnemy = new();
```

El nombre no deberá incluir palabras como `List`, `Collection` o `Dictionary` cuando el plural o el concepto de dominio ya permitan identificar claramente su contenido. El nombre deberá describir qué elementos contiene o qué relación representa, no la estructura concreta utilizada para almacenarlos (Microsoft, 2023a; Microsoft, 2026b).

### 4.3 Booleanos

Los identificadores booleanos deberán expresar una condición afirmativa. Cuando ayude a comprender su significado, se utilizarán prefijos como `Is`, `Has` o `Can`, respetando el tipo de capitalización correspondiente (Microsoft, 2023a; Microsoft, 2026b).

**Con estándar**

```csharp
bool isGameOver = false;
bool hasSpecialAbility = true;
bool canAttack = true;
```

**Sin estándar**

```csharp
bool gameOverFlag = false;
bool ability = true;
bool cannotAttack = false;
```

### 4.4 Declaración y sombreado de variables

Se deberá declarar una sola variable por línea para mejorar la claridad del código (Microsoft, 2025d).

**Con estándar**

```csharp
int playerScore = 0;
int enemyScore = 0;
```

**Sin estándar**

```csharp
int playerScore = 0, enemyScore = 0;
```

También deberá evitarse el sombreado, que ocurre cuando una variable local utiliza el mismo nombre que un campo de la clase (Microsoft, 2025d).

**Con estándar**

```csharp
private int _score;

public void AddScore(int earnedPoints) 
{
    int updatedScore = _score + earnedPoints;
    _score = updatedScore;
}
```

**Sin estándar**

```csharp
private int _score;

public void AddScore(int earnedPoints) 
{
    int _score = earnedPoints;
}
```

#### 4.4.1 Uso de `var`
Las variables locales deberán declarar su tipo de forma explícita. `var` solo podrá utilizarse cuando el lenguaje lo requiera, por ejemplo, para almacenar un tipo anónimo producido por una consulta LINQ. No se utilizará `var` con el resultado de un método, porque el tipo no puede determinarse únicamente al leer la asignación (Microsoft, 2025d; convención interna del equipo para restringir `var`).

Microsoft permite `var` cuando el tipo es evidente en el lado derecho de la asignación y desaconseja usarlo cuando el lector tendría que inferirlo a partir del nombre de un método. (Microsoft, 2025d).

**Con estándar**

```csharp
DamageResult damageResult = damageCalculator.Calculate(attack);
```

**Sin estándar**

```csharp
var damageResult = damageCalculator.Calculate(attack);
```

### 4.5 Campos privados e internos

Todos los campos privados o internos deberán escribirse utilizando `_camelCase`, sin cambiar el prefijo por tratarse de un campo estático. Por lo tanto, no se utilizará la convención `s_camelCase` (Microsoft, 2026b).

**Con estándar**

```csharp
private int _currentHealth;
private string _playerName;
private static int _activePlayers;
```

**Sin estándar**

```csharp
private int currentHealth;
private string PlayerName;
private static int s_activePlayers;
```

### 4.5.1 Inicialización de campos y métodos estáticos

Un campo estático solo se inicializará con un valor fijo, inmutable y conocido en tiempo de compilación mediante su declaración. Cuando la inicialización dependa de una operación (lectura de configuración, cálculo, acceso a otro tipo), se realizará dentro de un constructor estático (`static` sin modificador de acceso), nunca dentro de un constructor de instancia ni de un método público invocado manualmente para "inicializar" la clase.

Un constructor estático solo se justificará cuando el estado estático represente una responsabilidad genuinamente compartida por todas las instancias del tipo (un contador global, una caché compartida, un catálogo cargado una sola vez). Si el estado estático existe únicamente por conveniencia de acceso, deberá reconsiderarse el diseño e inyectar la dependencia en su lugar (Microsoft, s. f.-e; convención interna del equipo para justificar el estado estático).

**Con estándar**

```csharp

public sealed class EnemyCatalog
{
    private static readonly IReadOnlyDictionary<EnemyType, EnemyDefinition> _definitions;

    static EnemyCatalog()
    {
        _definitions = EnemyDefinitionLoader.LoadAll();
    }

    public static EnemyDefinition GetDefinition(EnemyType type)
    {
        return _definitions[type];
    }
}
```

**Sin estándar**

```csharp

public sealed class EnemyCatalog
{
    private static IReadOnlyDictionary<EnemyType, EnemyDefinition> _definitions;

    public EnemyCatalog()
    {
        _definitions = EnemyDefinitionLoader.LoadAll();
    }
}
```

### 4.6 Propiedades

Los nombres de las propiedades deberán escribirse en `PascalCase` y utilizar sustantivos, frases nominales o adjetivos que describan el dato representado. No se agregarán los prefijos `Get` o `Set`, porque la lectura y la escritura ya se expresan mediante los accesores de la propiedad (Microsoft, 2023a; Microsoft, 2025f).

Se utilizará la forma de acceso que corresponda al ciclo de vida del valor (Microsoft, 2024b; Microsoft, 2025f):

- `{ get; set; }`: únicamente cuando cualquier consumidor autorizado pueda leer y modificar el valor, como en un DTO.
- `{ get; private set; }`: cuando el valor pueda consultarse públicamente, pero solo la propia clase deba modificarlo.
- `{ get; protected set; }`: cuando la clase y sus tipos derivados puedan modificarlo.
- `{ get; init; }`: cuando el valor solo deba asignarse durante la construcción o inicialización del objeto.
- `{ get; }`: cuando el valor solo pueda asignarse desde un constructor.

Un modificador aplicado a un accesor deberá ser más restrictivo que el modificador de la propiedad. Microsoft documenta que `get` y `set` son accesores y que es habitual restringir `set` para conservar una lectura pública sin permitir modificaciones externas (Microsoft, 2024b; Microsoft, 2025f).

**Con estándar**

```csharp
public int CurrentHealth { get; private set; }
public string CharacterName { get; private set; }
public bool IsInvulnerable { get; private set; }
public Guid PlayerId { get; init; }
```

**Sin estándar**

```csharp
public int currentHealth { get; private set; }
public string character_name { get; private set; }
public bool InvulnerabilityFlag { get; private set; }
public Guid GetPlayerId { get; set; }
```

Las propiedades booleanas deberán expresar condiciones afirmativas y las propiedades de colecciones deberán utilizar nombres en plural. Estas recomendaciones aparecen en las convenciones oficiales para miembros de tipos (Microsoft, 2023a).

**Propiedades automáticas**

Una propiedad se declarará como autoimplementada ({ get; set; } sin cuerpo) cuando no requiera validación, transformación ni reacción al cambio de valor. En cuanto la propiedad necesite cualquiera de esos comportamientos, dejará de ser autoimplementada y pasará a seguir la regla 4.6.1 (campo de respaldo explícito). No se creará un campo de respaldo manual para una propiedad que no lo necesite, ya que duplica código que el compilador genera automáticamente (Microsoft, s. f.-g).

**Con estándar**

```csharp
public sealed class WeaponData
{
    public string Name { get; init; }
    public int DamageMultiplier { get; init; }
}
```

**Sin estándar**

```csharp
public sealed class WeaponData
{
    private string _name;
    private int _damageMultiplier;

    public string Name
    {
        get { return _name; }
        init { _name = value; }
    }

    public int DamageMultiplier
    {
        get { return _damageMultiplier; }
        init { _damageMultiplier = value; }
    }
}
```

**Propiedades privadas**

Una propiedad podrá declararse private cuando exponga una conveniencia de solo lectura o de acceso interno para la propia clase (por ejemplo, derivar un valor reutilizado varias veces dentro de la clase), sin que forme parte del contrato público del tipo. Una propiedad privada seguirá las mismas reglas de nombrado, PascalCase, que una propiedad pública; no se confundirá con un campo privado, que usa _camelCase según la regla 4.5 (Microsoft, s. f.-g).

**Con estándar**

```csharp
public sealed class DamageCalculator
{
    private int TotalModifiers => _criticalBonus + _elementalBonus;

    private readonly int _criticalBonus;
    private readonly int _elementalBonus;

    public int Calculate(int baseDamage)
    {
        return baseDamage + TotalModifiers;
    }
}
```

**Sin estándar**

```csharp
public sealed class DamageCalculator
{
    private int _totalModifiers => _criticalBonus + _elementalBonus;
}
```

### 4.6.1 Propiedades con campo de respaldo

Cuando asignar un valor requiera una validación o transformación breve, la propiedad deberá utilizar un campo de respaldo explícito y accesores `get` y `set`. Los accesores no deberán ejecutar operaciones de dominio, emitir eventos, escribir logs ni realizar entrada o salida. Los cambios que representen acciones del juego deberán exponerse mediante métodos, como `ReceiveDamage` o `RestoreHealth` (Microsoft, 2025f; convención interna del equipo sobre operaciones de dominio).

El campo de respaldo deberá ser privado, utilizar `_camelCase` y no exponerse directamente. Las propiedades permiten ocultar la verificación del valor y restringir la accesibilidad de la escritura sin cambiar la forma en que el consumidor consulta el dato (Microsoft, 2025f).

**Con estándar**

```csharp
private const int MinimumHealth = 0;
private const int MaxHealth = 100;
private int _currentHealth;

public int CurrentHealth
{
    get
    {
        return _currentHealth;
    }
    set
    {
        _currentHealth = Math.Clamp(value, MinimumHealth, MaxHealth);
    }
}
```

**Sin estándar**

```csharp
private int currentHealth;

public int CurrentHealth
{
    get
    {
        return currentHealth;
    }
    set
    {
        currentHealth = value;
        OnHealthChanged?.Invoke(currentHealth);
    }
}
```

### 4.6.2 Propiedades calculadas

Cuando el valor de una propiedad se derive por completo de otros campos o propiedades, en lugar de almacenarse por sí mismo, se declarará como una propiedad de solo lectura sin campo de respaldo, utilizando un cuerpo de expresión (=>). Este tipo de propiedad no deberá tener accesor set, init ni backing field propio, ya que su valor siempre se recalcula a partir del estado existente.

Una propiedad calculada nunca deberá ejecutar operaciones costosas, de entrada/salida, ni con efectos secundarios, dado que puede evaluarse en cualquier momento y un número indeterminado de veces. Si el cálculo requiere una operación costosa, deberá exponerse como un método en lugar de una propiedad (Microsoft, 2025f).

**Con estándar**

```csharp
private const int MinimumHealth = 0;

private int _currentHealth;

public bool IsAlive => _currentHealth > MinimumHealth;
````

**Sin estándar**

```csharp

private int _currentHealth;
private bool _isAlive;

public bool IsAlive
{
    get
    {
        return _isAlive;
    }
    set
    {
        _isAlive = value;
    }
}

```

### 4.7 Constantes

Las constantes de C# deberán escribirse en `PascalCase`. Esta regla se aplicará tanto a constantes públicas como privadas y locales (Microsoft, 2026b).

**Con estándar**

```csharp
private const int MaximumLives = 3;
```

**Sin estándar**

```csharp
private const int MAXIMUM_LIVES = 3;
```

Las constantes deberán representar valores que no cambien durante la ejecución (Microsoft, 2025d).

### 4.8 Métodos

Los métodos y las funciones locales deberán escribirse utilizando `PascalCase`. Sus nombres deberán ser verbos o frases verbales que indiquen claramente la acción que realizan (Microsoft, 2023a; Microsoft, 2026b).

**Con estándar**

```csharp
private const int MinimumDamage = 0;

public int CalculateDamage(int baseDamage, int defensePoints) 
{
    int calculatedDamage = baseDamage - defensePoints;

    if (calculatedDamage < MinimumDamage) 
    {
        calculatedDamage = MinimumDamage;
    }

    return calculatedDamage;
}
```

**Sin estándar**

```csharp
private const int MinimumDamage = 0;

public int calculateDamage(int baseDamage, int defensePoints) 
{
    int calculatedDamage = baseDamage - defensePoints;

    if (calculatedDamage < MinimumDamage) 
    {
        calculatedDamage = MinimumDamage;
    }

    return calculatedDamage;
}
```

### 4.9 Eventos

Los eventos deberán escribirse utilizando `PascalCase` y nombrarse con verbos o frases verbales. Se utilizará el presente para eventos que ocurren antes de una acción y el pasado para los que ocurren después (Microsoft, 2023a).

Por ejemplo:

- `PlayerDying`: se ejecuta antes de que el personaje muera.
- `PlayerDied`: se ejecuta después de que el personaje haya muerto.

**Con estándar**

```csharp
public event EventHandler<PlayerDiedEventArgs>? PlayerDied;

protected virtual void OnPlayerDied(PlayerDiedEventArgs e) 
{
    PlayerDied?.Invoke(this, e);
}
```

**Sin estándar**

```csharp
public event EventHandler<PlayerDiedEventArgs>? AfterPlayerDeath;

protected virtual void RaiseDeath(PlayerDiedEventArgs data) 
{
    AfterPlayerDeath?.Invoke(this, data);
}
```

Los métodos protegidos que disparen un evento deberán comenzar con `On`, seguido del nombre del evento. Los parámetros de un manejador de eventos deberán llamarse `sender` y `e`, de acuerdo con las convenciones oficiales para miembros de tipos de .NET (Microsoft, 2023a).

### 4.10 Métodos de prueba unitaria

Los métodos de prueba deberán utilizar el siguiente formato (Microsoft, 2025b; convención interna del equipo):

```csharp
Test_MethodName_Scenario_ExpectedResult
```

Cada parte tendrá la siguiente función (Microsoft, 2025b; convención interna del equipo):

- `Test`: prefijo obligatorio que identifica el método como una prueba.
- `MethodName`: nombre exacto del método que se está probando.
- `Scenario`: condición o escenario evaluado.
- `ExpectedResult`: comportamiento observable esperado.

Todas las partes del nombre deberán escribirse en inglés, utilizar `PascalCase` y separarse mediante guiones bajos (Microsoft, 2025b; convención interna del equipo).

**Con estándar**

```csharp
public void Test_CalculateDamage_DamageBelowDefense_ReturnsMinimumDamage() 
{ 
}
```

**Sin estándar**

```csharp
public void testDamage1() 
{
}
```

Las partes `MethodName`, `Scenario` y `ExpectedResult` coinciden con la recomendación de que el nombre de una prueba describa el método probado, el escenario y el comportamiento esperado. El prefijo `Test` es una convención propia del equipo (Microsoft, 2025b).

### 4.11 Clases, estructuras y registros

Los nombres de clases, estructuras y registros deberán escribirse utilizando `PascalCase`. Deberán ser sustantivos o frases nominales que describan la entidad o concepto que representan (Microsoft, 2025e; Microsoft, 2026b).

**Con estándar**

```csharp
public class PlayerInventory 
{ 
}

public struct DamageResult 
{ 
}
```

**Sin estándar**

```csharp
public class player_inventory 
{ 
}

public struct damage_result 
{ 
}
```

### 4.12 Interfaces

Las interfaces deberán escribirse utilizando `PascalCase` y comenzar con la letra mayúscula `I` (Microsoft, 2025e; Microsoft, 2026b).

**Con estándar**

```csharp
public interface IEnemySpawner 
{
    Enemy Spawn(EnemySpawnRequest request);
}
```

**Sin estándar**

```csharp
public interface EnemySpawnerInterface 
{
    Enemy Generate(EnemySpawnRequest request);
}
```

Cuando una clase sea la implementación principal de una interfaz, sus nombres deberán diferenciarse únicamente por el prefijo `I` (Microsoft, 2025e).

**Con estándar**

```csharp
public interface IEnemySpawner 
{
    Enemy Spawn(EnemySpawnRequest request);
}

public class EnemySpawner : IEnemySpawner 
{
    public Enemy Spawn(EnemySpawnRequest request)
    {
        Enemy enemy = new Enemy(request.Type);

        return enemy;
    }
}
```

**Sin estándar**

```csharp
public interface SpawnerInterface 
{
    Enemy Generate(EnemySpawnRequest request);
}

public class DefaultEnemyGenerator : SpawnerInterface 
{
    public Enemy Generate(EnemySpawnRequest request)
    {
        Enemy enemy = new Enemy(request.Type);

        return enemy;
    }
}
```

Las reglas para clases e interfaces están recogidas en las guías oficiales de diseño de .NET (Microsoft, 2025e).

### 4.13 Parámetros de tipo genérico

Los parámetros genéricos deberán comenzar con la letra mayúscula `T`. Se podrá utilizar únicamente `T` cuando el significado sea evidente o un nombre descriptivo como `TEntity` cuando proporcione mayor claridad (Microsoft, 2026b).

**Con estándar**

```csharp
public class ObjectPool<TEntity> 
{ 
}
```

**Sin estándar**

```csharp
public class ObjectPool<EntityType> 
{ 
}
```

### 4.14 Enumeraciones

Los nombres de las enumeraciones y sus valores deberán escribirse utilizando `PascalCase` (Microsoft, 2025e; Microsoft, 2026b).

Las enumeraciones normales deberán utilizar un nombre singular. Las enumeraciones que representen una combinación de indicadores deberán utilizar un nombre plural. No se agregarán los sufijos `Enum`,`Flag` o `Flags` (Microsoft, 2025e).

**Con estándar**

```csharp
public enum EnemyState 
{
    Idle,
    Patrolling,
    Attacking
}
```

**Sin estándar**

```csharp
public enum EnemyStateEnum 
{
    IDLE,
    PATROLLING,
    ATTACKING
}
```

### 4.15 Espacios de nombres

Los espacios de nombres deberán utilizar `PascalCase`. Sus componentes se separarán mediante puntos y deberán representar de forma clara el proyecto y la funcionalidad agrupada (Microsoft, 2026b).

**Con estándar**

```csharp
namespace CompanyName.GameName.Combat;
```

**Sin estándar**

```csharp
namespace company_name.game_name.combat;
```

### 4.16 Sufijos oficiales por responsabilidad

Se utilizarán los siguientes sufijos cuando el tipo cumpla realmente con la responsabilidad correspondiente (Microsoft, 2025e):

- `Exception`: excepciones personalizadas.
- `EventArgs`: clases que contienen información de un evento.
- `EventHandler`: delegados personalizados utilizados para eventos.
- `Attribute`: atributos personalizados.
- `Stream`: tipos especializados de flujo de datos.

No se agregarán los sufijos `Collection` o `Dictionary` únicamente para indicar la estructura de almacenamiento. Si se crea un tipo especializado, su nombre deberá expresar la responsabilidad de dominio, por ejemplo, `Inventory` o `EnemyRegistry` (Microsoft, 2025e).

**Con estándar**

```csharp
public sealed class InsufficientManaException : Exception 
{ 
}

public sealed class DamageReceivedEventArgs : EventArgs 
{ 
}
```

**Sin estándar**

```csharp
public sealed class InsufficientManaError : Exception 
{ 
}

public sealed class DamageReceivedData : EventArgs 
{ 
}
```

**Sufijos arquitectónicos**

Además de los sufijos por responsabilidad técnica ya definidos, se utilizarán los siguientes sufijos para identificar la capa arquitectónica de un tipo, siempre que el tipo cumpla realmente con esa responsabilidad:

- `Service`: orquesta lógica de aplicación, coordinando entidades y repositorios.
- `Repository`: encapsula el acceso a datos persistentes de un agregado.
- `Factory`: encapsula la creación de instancias complejas.
- `Manager`: coordina el ciclo de vida de un conjunto de objetos relacionados en tiempo de ejecución (por ejemplo, EnemyManager).
- `Controller`: coordina la entrada del jugador o de la red hacia el dominio, sin contener lógica de negocio propia.
- `Provider`: expone un valor o recurso obtenido de una fuente externa o configurable.

No se combinarán dos sufijos arquitectónicos en el mismo nombre (por ejemplo, `PlayerServiceManager`), ya que indica que la clase tiene más de una responsabilidad (Martin, 2008).

**Con estándar**

```csharp
public sealed class SaveGameService
{
}

public sealed class SaveGameRepository : ISaveGameRepository
{
}
```

**Sin estándar**

```csharp
public sealed class SaveGameServiceManager
{
}
```

### 4.17 Nombrado de la base de datos 

Los nombres de tablas, columnas, vistas, procedimientos almacenados y demás objetos de la base de datos se escribirán en inglés, manteniendo consistencia con el resto de los identificadores del proyecto definidos en la sección 1.3. Los nombres deberán ser claros y describir el dato o la entidad que representan, evitando abreviaturas innecesarias.

Las tablas se nombrarán en PascalCase y en plural, siguiendo el mismo criterio utilizado para las colecciones en la sección 4.2. Las columnas se nombrarán en PascalCase y en singular, salvo que representen por sí mismas una colección de valores.

**Con estándar**

```sql

CREATE TABLE Players
(
    PlayerId INT PRIMARY KEY,
    PlayerName NVARCHAR(50) NOT NULL,
    CurrentHealth INT NOT NULL
);
```

**Sin estándar**

```sql

CREATE TABLE jugadores
(
    id_jugador INT PRIMARY KEY,
    nombre_jugador NVARCHAR(50) NOT NULL,
    vida_actual INT NOT NULL
);

```

## 5 Estilo de código

El código deberá mantener un formato uniforme que facilite su lectura, revisión y mantenimiento. Las reglas de esta sección se aplicarán a todos los archivos (Microsoft, 2025c; Microsoft, 2025d).

Se utilizarán cuatro espacios para la indentación, llaves con estilo Allman, una instrucción por línea y líneas de continuación indentadas. Estas reglas toman como base las convenciones de código oficiales de C# (Microsoft, 2025d).

### 5.1 Formato general (indentación, límite de columnas)

**Indentación de cuatro espacios**

Por cada nivel de indentación se utilizarán cuatro espacios (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
public sealed class EnemyController
{
    public void UpdateEnemy(Enemy enemy)
    {
        if (enemy.IsAlive)
        {
            enemy.Move();
        }
    }
}
```

**Sin estándar**

```csharp
public sealed class EnemyController
{
  public void UpdateEnemy(Enemy enemy)
  {
    if (enemy.IsAlive)
    {
      enemy.Move();
    }
  }
}
```

**Uso de espacios en lugar de tabuladores**

La indentación deberá realizarse con espacios. No se utilizarán tabuladores, ya que su anchura puede cambiar entre editores (Microsoft, 2025c; Microsoft, 2025d).

**Colocación de llaves**

Las llaves deberán seguir el estilo Allman. La llave de apertura y la llave de cierre se colocarán en líneas independientes y alineadas con la declaración correspondiente (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
public void HealPlayer()
{
    player.RestoreHealth();
}
```

**Sin estándar**

```csharp
public void HealPlayer() {
    player.RestoreHealth();
}
```

**Una instrucción por línea**

Cada línea deberá contener una sola instrucción (Microsoft, 2025d).

**Con estándar**

```csharp
player.ReceiveDamage(damage);
enemy.StartAttack();
```

**Sin estándar**

```csharp
player.ReceiveDamage(damage); enemy.StartAttack();
```

**Una declaración por línea**

Cada variable deberá declararse en una línea independiente (Microsoft, 2025d).

**Con estándar**

```csharp
int currentHealth = player.Health;
int maximumHealth = player.MaximumHealth;
```

**Sin estándar**

```csharp
int currentHealth = player.Health, maximumHealth = player.MaximumHealth;
```

**Límite de 120 caracteres**

Ninguna línea deberá superar los 120 caracteres. Cuando una instrucción exceda el límite, deberá dividirse en varias líneas (McConnell, 2004; convención interna del equipo para el límite de 120 caracteres).

**Con estándar**

```csharp
BattleResult battleResult = battleService.ResolveBattle(
    selectedDifficulty,
    currentLevel,
    battleRules);
```

**Sin estándar**

```csharp
BattleResult battleResult = battleService.ResolveBattle(selectedDifficulty, currentLevel, battleRules);
```

**Indentación de líneas de continuación**

Las líneas de continuación deberán indentarse cuatro espacios adicionales respecto de la línea original. Cuando una expresión se divida antes de un operador, todos los operadores deberán mantener la misma alineación (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
int totalDamage = baseDamage
    + criticalDamage
    + elementalDamage;
```

**Sin estándar**

```csharp
int totalDamage = baseDamage
+ criticalDamage
+ elementalDamage;
```

**Distribución de argumentos**

Cuando una llamada deba dividirse por superar el límite de columna, se colocará un argumento por línea. El paréntesis de cierre se alineará con el inicio de la instrucción (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
Enemy enemy = enemyFactory.Create(
    enemyType,
    spawnPosition,
    initialHealth);
```

**Sin estándar**

```csharp
Enemy enemy = enemyFactory.Create(enemyType,
    spawnPosition, initialHealth);
```

### 5.2 Espacios en blanco (vertical/horizontal)

**Separación entre secciones del archivo**

Se dejará una línea en blanco entre el bloque de directivas `using`, la declaración del espacio de nombres y la declaración del tipo (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
using System.Collections.Generic;

namespace AdventureGame.Characters;

public sealed class Player
{
}
```

**Sin estándar**

```csharp
using System.Collections.Generic;
namespace AdventureGame.Characters;
public sealed class Player
{
}
```

**Separación entre grupos de miembros**

Se dejará una línea en blanco entre campos, constructores, propiedades y métodos cuando pertenezcan a grupos distintos (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
private int _health;

public Player(int initialHealth)
{
    _health = initialHealth;
}
```

**Sin estándar**

```csharp
private int _health;
public Player(int initialHealth)
{
    _health = initialHealth;
}
```

**Separación entre métodos**

Se dejará una línea en blanco entre dos métodos consecutivos (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
public void Attack()
{
    weapon.Use();
}

public void Defend()
{
    shield.Activate();
}
```

**Sin estándar**

```csharp
public void Attack()
{
    weapon.Use();
}
public void Defend()
{
    shield.Activate();
}
```

**Separación de etapas lógicas**

Dentro de un método se utilizará una línea en blanco cuando sea necesario distinguir dos etapas lógicas de una operación (Microsoft, 2025d; McConnell, 2004).

**Con estándar**

```csharp
public void CompleteLevel()
{
    int earnedScore = scoreCalculator.Calculate(player, level);
    player.AddScore(earnedScore);

    rewardService.GrantRewards(player, level);
    level.MarkAsCompleted();
}
```

**Sin estándar**

```csharp
public void CompleteLevel()
{
    int earnedScore = scoreCalculator.Calculate(player, level);
    player.AddScore(earnedScore);
    rewardService.GrantRewards(player, level);
    level.MarkAsCompleted();
}
```

**Cantidad de líneas en blanco**

No se utilizarán varias líneas en blanco consecutivas. Una sola línea será suficiente para separar bloques relacionados (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
private int _health;

public int Health
{
    get
    {
        return _health;
    }
}
```

**Sin estándar**

```csharp
private int _health;



public int Health
{
    get
    {
        return _health;
    }
}
```

**Espacio después de palabras clave**

Se colocará un espacio después de las palabras clave `if`, `for`, `foreach`, `while`, `switch`, `catch` y `using` cuando estén seguidas de una expresión (Microsoft, 2025c).

**Con estándar**

```csharp
if (player.IsAlive)
{
    player.Update();
}
```

**Sin estándar**

```csharp
if(player.IsAlive)
{
    player.Update();
}
```

**Espacios alrededor de operadores binarios**

Se colocará un espacio a cada lado de los operadores binarios, como `=`, `+`, `-`,`==`, `!=`, `&&` y `||` (Microsoft, 2025c).

**Con estándar**

```csharp
int totalDamage = baseDamage + bonusDamage;
```

**Sin estándar**

```csharp
int totalDamage=baseDamage+bonusDamage;
```

**Espacio entre un método y su paréntesis**

No se colocará un espacio entre el nombre de un método y el paréntesis de apertura (Microsoft, 2025c).

**Con estándar**

```csharp
player.RestoreHealth();
```

**Sin estándar**

```csharp
player.RestoreHealth ();
```

**Espacios dentro de paréntesis**

No se colocarán espacios inmediatamente después de un paréntesis de apertura ni antes de uno de cierre (Microsoft, 2025c).

**Con estándar**

```csharp
enemy.ReceiveDamage(damage);
```

**Sin estándar**

```csharp
enemy.ReceiveDamage( damage );
```

**Espacio después de comas**

Se colocará un espacio después de cada coma que separe argumentos, parámetros o elementos (Microsoft, 2025c).

**Con estándar**

```csharp
MovePlayer(horizontalDirection, verticalDirection);
```

**Sin estándar**

```csharp
MovePlayer(horizontalDirection,verticalDirection);
```

**Espaciado de operadores unarios**

Los operadores unarios, como `!`, `++` y `--`, no se separarán de su operando (Microsoft, 2025c).

**Con estándar**

```csharp
remainingEnemies--;
```

**Sin estándar**

```csharp
remainingEnemies --;
```

**Alineación manual con espacios**

No se agregarán espacios adicionales para alinear declaraciones manualmente. Cada elemento deberá conservar únicamente el espacio requerido por la sintaxis (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
int currentHealth = player.Health;
string playerName = player.Name;
```

**Sin estándar**

```csharp
int    currentHealth = player.Health;
string playerName    = player.Name;
```

### 5.3 Organización del archivo (orden de `using`)

**Ubicación de las directivas `using`**

Las directivas `using` deberán colocarse fuera de la declaración del espacio de nombres (Microsoft, 2025d).

**Con estándar**

```csharp
using System.Collections.Generic;

namespace AdventureGame.Inventory;

public sealed class Inventory
{
}
```

**Sin estándar**

```csharp
namespace AdventureGame.Inventory
{
    using System.Collections.Generic;

    public sealed class Inventory
    {
    }
}
```

**Orden de las directivas `using`**

Las directivas formarán un único bloque continuo, sin líneas en blanco entre ellas. Primero se colocarán los espacios de nombres del sistema, después los de bibliotecas externas y finalmente los pertenecientes al proyecto (Microsoft, 2025d; convención interna del equipo para la agrupación).

**Con estándar**

```csharp
using System.Collections.Generic;
using PathfindingLibrary;
using AdventureGame.Characters;
```

**Sin estándar**

```csharp
using AdventureGame.Characters;
using System.Collections.Generic;
using PathfindingLibrary;
```

**Orden alfabético dentro de cada grupo**

Las directivas `using` deberán ordenarse alfabéticamente dentro del grupo al que pertenezcan (Microsoft, 2025d).

**Con estándar**

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
```

**Sin estándar**

```csharp
using System.Linq;
using System;
using System.Collections.Generic;
```

**Bloque continuo de directivas `using`**

No se insertarán líneas en blanco dentro del bloque de directivas `using` (Microsoft, 2025d; convención interna del equipo).

**Con estándar**

```csharp
using System.Collections.Generic;
using PathfindingLibrary;
using AdventureGame.Characters;
```

**Sin estándar**

```csharp
using System.Collections.Generic;

using PathfindingLibrary;

using AdventureGame.Characters;
```

**Directivas duplicadas o sin utilizar**

No se conservarán directivas `using` duplicadas ni directivas que no sean utilizadas por el archivo (Microsoft, 2025d).

**Con estándar**

```csharp
using System.Collections.Generic;

namespace AdventureGame.Inventory;

public sealed class Inventory
{
    private readonly List<Item> _items = new List<Item>();
}
```

**Sin estándar**

```csharp
using System.Collections.Generic;
using System.Collections.Generic;
using System.Text;

namespace AdventureGame.Inventory;

public sealed class Inventory
{
    private readonly List<Item> _items = new List<Item>();
}
```

**Alias y directivas `using static`**

Los alias y las directivas `using static` se colocarán después de las directivas ordinarias. Solo se utilizarán cuando eviten una ambigüedad o mejoren claramente la lectura (Microsoft, 2025d; convención interna del equipo para el orden).

**Con estándar**

```csharp
using System;
using AdventureGame.Characters;
using DamageCalculator = AdventureGame.Combat.DamageCalculator;
using static AdventureGame.Combat.DamageConstants;
```

**Sin estándar**

```csharp
using static AdventureGame.Combat.DamageConstants;
using DamageCalculator = AdventureGame.Combat.DamageCalculator;
using AdventureGame.Characters;
using System;
```

**Declaración del espacio de nombres**

Se utilizará una declaración de espacio de nombres con ámbito de archivo para evitar un nivel de indentación innecesario (Microsoft, 2025d).

**Con estándar**

```csharp
namespace AdventureGame.Characters;

public sealed class Enemy
{
}
```

**Sin estándar**

```csharp
namespace AdventureGame.Characters
{
    public sealed class Enemy
    {
    }
}
```

**Cantidad de tipos públicos por archivo**

Cada archivo deberá contener un único tipo público principal. El nombre del archivo deberá coincidir con el nombre de ese tipo (Microsoft, 2025d; convención interna del equipo).

**Con estándar — archivo `EnemyManager.cs`**

```csharp
namespace AdventureGame.Enemies;

public sealed class EnemyManager
{
}
```

**Sin estándar — archivo `EnemyManager.cs`**

```csharp
namespace AdventureGame.Enemies;

public sealed class EnemyManager
{
}

public sealed class EnemyFactory
{
}
```

### 5.4 Orden de miembros de la clase

Los miembros de una clase deberán conservar el siguiente orden general (Microsoft, 2025d; convención interna del equipo):

1. Constantes.
2. Campos estáticos.
3. Campos de instancia.
4. Constructores.
5. Eventos.
6. Propiedades.
7. Métodos públicos.
8. Métodos protegidos.
9. Métodos privados.
10. Tipos anidados.

Los ejemplos de esta regla deberán mostrar la clase completa para que el orden de todos los grupos pueda evaluarse en conjunto (Microsoft, 2025d; convención interna del equipo).

**Con estándar**

```csharp
public sealed class PlayerController
{
    private const int DefaultHealth = 100;

    private static int _activePlayers;

    private readonly Weapon _weapon;

    public PlayerController(Weapon weapon)
    {
        _weapon = weapon;
        CurrentHealth = DefaultHealth;
        _activePlayers++;
    }

    public event Action? PlayerDefeated;

    public int CurrentHealth { get; private set; }

    public void Attack()
    {
        PrepareAttack();
        ExecuteAttack();
    }

    protected void PrepareAttack()
    {
        _weapon.Prepare();
    }

    private void ExecuteAttack()
    {
        _weapon.Use();
    }

    private enum PlayerState
    {
        Idle,
        Attacking,
        Defeated
    }
}
```

**Sin estándar**

```csharp
public sealed class PlayerController
{
    private enum PlayerState
    {
        Idle,
        Attacking,
        Defeated
    }

    private void ExecuteAttack()
    {
        _weapon.Use();
    }

    public int CurrentHealth { get; private set; }

    public event Action? PlayerDefeated;

    public PlayerController(Weapon weapon)
    {
        _weapon = weapon;
        CurrentHealth = DefaultHealth;
        _activePlayers++;
    }

    private readonly Weapon _weapon;

    private static int _activePlayers;

    private const int DefaultHealth = 100;
}
```

## 6. Estructuras de control

### 6.1 Llaves

El uso de llaves será obligatorio en la totalidad de las estructuras de control (if, else, for, while, do-while, switch), sin excepción para bloques que contengan una única instrucción (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
private const int NoDamage = 0;

if (amount > NoDamage)
{
    _currentHealth -= amount;
}
```

**Sin estándar**

```csharp
if (amount > 0)
    _currentHealth -= amount;
```

### 6.2 Condicionales

La palabra clave `if` y su expresión condicional deben ir en la misma línea. Cuando exista un `else` o `else if`, la palabra clave `else` se escribirá en su propia línea, nunca compartiendo línea con la llave de cierre del bloque anterior (Microsoft, 2025c; Microsoft, 2025d).

**Con estándar**

```csharp
private const int MinimumHealth = 0;

if (_currentHealth <= MinimumHealth)
{
    TriggerDefeat();
}
else
{
    TriggerAlive();
}
```

**Sin estándar**

```csharp
if (_currentHealth <= 0)
{
    TriggerDefeat();
} else
{
    TriggerAlive();
}
```

### 6.3 Bucles

La cláusula de inicialización de un bucle `for` no deberá declarar ni actualizar más de tres variables. Adicionalmente, un bucle que se ejecute una vez por cuadro o con alta frecuencia deberá evitar operaciones que creen objetos, cadenas o colecciones nuevas en cada iteración cuando esas asignaciones puedan reutilizarse (Martin, 2008; convención interna del equipo para el máximo de variables).

**Con estándar**

```csharp
for (int enemyIndex = 0; enemyIndex < activeEnemies.Length; enemyIndex++)
{
    ApplyPoisonTick(activeEnemies[enemyIndex]);
}
```

**Sin estándar**

```csharp
for (int enemyIndex = 0, tickCount = 0, totalDamage = 0, poisonStacks = 0; enemyIndex < activeEnemies.Length; enemyIndex++)
{
    ApplyPoisonTick(activeEnemies[enemyIndex]);
}
```

### 6.4 Sentencia `switch` y expresión `switch`

**Sentencia `switch`**

Toda sentencia `switch` deberá incluir una etiqueta `default`. Cada sección con instrucciones deberá terminar explícitamente con `break`, `return`, `throw`. La etiqueta `default` obligatoria es una política de legibilidad del equipo (Microsoft, 2026c; convención interna del equipo para la obligatoriedad de `default`).

**Con estándar**

```csharp
switch (currentGameState)
{
    case GameState.Menu:
        ShowMainMenu();
        break;
    case GameState.Playing:
        ResumeGameplay();
        break;
    default:
        LoadSplashScreen();
        break;
}
```

**Sin estándar**

```csharp
switch (currentGameState)
{
    case GameState.Menu:
        ShowMainMenu();
    case GameState.Playing:
        ResumeGameplay();
        break;
}
```

### 6.5 Operador ternario

El operador ternario (condición ? valorSiVerdadero : valorSiFalso) solo podrá utilizarse cuando la condición sea una única expresión booleana simple, sin más de un operador lógico. Ambas ramas deben ser expresiones del mismo tipo que retornen un valor; no se permite invocar métodos void en ninguna rama. Se prohíbe anidar operadores ternarios (Microsoft, 2025d; convención interna del equipo para la complejidad permitida).

**Con estándar**

```csharp
string statusLabel = _isGameOver ? "Game Over" : "Playing";
```

**Sin estándar**

```csharp
string statusLabel = (_isGameOver && _livesRemaining <= 0 && !_isRespawning) ? "Game Over" : "Playing";
```

## 7. Manejo de errores y excepciones

### 7.1 Uso y selección de excepciones

Las excepciones se utilizarán únicamente en servicios y componentes de infraestructura, donde una operación pueda fallar por una condición verdaderamente excepcional. Las entidades, objetos de valor y componentes de presentación no utilizarán excepciones para representar resultados esperados del juego, como un inventario lleno, una habilidad en enfriamiento o una acción no disponible; esos casos se comunicarán mediante valores de retorno o tipos de resultado (Microsoft, 2025a; convención interna del equipo para limitar las capas que lanzan excepciones).

Antes de crear una excepción personalizada, se utilizará el tipo estándar que describa con mayor precisión el error. No se lanzarán excepciones para controlar el flujo normal. Microsoft recomienda evitar excepciones para condiciones frecuentes, seleccionar tipos predefinidos y reservar `try`/`catch` para errores de los que el código pueda recuperarse (Microsoft, 2025a; Microsoft, 2023b).

| Excepción | Cuándo se utilizará en un servicio |
| --- | --- |
| `ArgumentNullException` | Un parámetro obligatorio recibido por el servicio es `null`. |
| `ArgumentException` | Un argumento tiene un valor o formato inválido que no corresponde a un rango numérico. |
| `ArgumentOutOfRangeException` | Un argumento se encuentra fuera del intervalo permitido. |
| `InvalidOperationException` | El estado actual del objeto no permite ejecutar la operación solicitada. |
| `NotSupportedException` | La operación forma parte del contrato, pero la implementación no la admite. |
| `ObjectDisposedException` | Se intenta utilizar un recurso que el servicio ya liberó. |
| `IOException` | Falla una operación de lectura, escritura o acceso a archivos. |
| `UnauthorizedAccessException` | El proceso no tiene permisos para acceder al recurso solicitado. |
| `TimeoutException` | Una operación externa no termina dentro del tiempo permitido. |
| `OperationCanceledException` | La operación se cancela mediante el mecanismo de cancelación previsto. |

No se lanzarán directamente `Exception`, `SystemException`, `NullReferenceException`, `IndexOutOfRangeException`, `StackOverflowException`, `AccessViolationException` ni `OutOfMemoryException`. `NotImplementedException` solo podrá utilizarse temporalmente durante el desarrollo y deberá eliminarse antes de integrar el código a la rama principal (Microsoft, 2023b; Microsoft, 2025a).

**Con estándar**

```csharp
public sealed class SaveGameService
{
    private readonly ISaveGameRepository _saveGameRepository;

    public SaveGameService(ISaveGameRepository saveGameRepository)
    {
        ArgumentNullException.ThrowIfNull(saveGameRepository);
        _saveGameRepository = saveGameRepository;
    }

    public void Save(PlayerState playerState)
    {
        ArgumentNullException.ThrowIfNull(playerState);

        if (!playerState.CanBeSaved)
        {
            throw new InvalidOperationException(
                "The player state cannot be saved in its current state.");
        }

        _saveGameRepository.Save(playerState);
    }
}
```

**Sin estándar**

```csharp
public sealed class Player
{
    public void UseItem(Item? item)
    {
        if (item is null)
        {
            throw new Exception("Invalid item.");
        }
    }
}
```

#### 7.1.1 Excepciones personalizadas

Solo se creará una excepción personalizada cuando un consumidor necesite distinguir ese fallo de las excepciones estándar para manejarlo de manera diferente. La clase deberá derivar de `Exception`, terminar con el sufijo `Exception` e incluir los constructores sin parámetros, con mensaje y con mensaje más excepción interna. No se agregará el constructor de serialización heredado de `Exception`, porque las API de serialización de excepciones están obsoletas en .NET moderno (Microsoft, 2025a; Microsoft, 2023c).

**Con estándar**

```csharp
public sealed class SaveGameException : Exception
{
    public SaveGameException()
    {
    }

    public SaveGameException(string message) : base(message)
    {
    }

    public SaveGameException(
        string message,
        Exception innerException) : base(message, innerException)
    {
    }
}
```

**Sin estándar**

```csharp
public class SaveError : ApplicationException
{
    public SaveError(string message) : base(message)
    {
    }
}
```

### 7.2 `try`, `catch`, `finally` y relanzamiento

Los bloques `catch` nunca deberán quedar vacíos. Se capturará el tipo más específico posible y las cláusulas se ordenarán desde la excepción más derivada hasta la menos derivada. Si el servicio no puede recuperarse, no deberá capturar la excepción. Una excepción capturada deberá manejarse, registrarse, relanzarse mediante `throw;` o envolverse conservando la excepción original en `InnerException` (Microsoft, 2025a; Microsoft, 2026a).

No se capturarán `Exception` ni `SystemException` en servicios ordinarios. `Exception` solo podrá capturarse en el límite superior de la aplicación para registrar un fallo no controlado y terminar o propagar la operación de forma segura. `SystemException` no deberá capturarse de forma explícita. Para preservar la traza original se utilizará `throw;`, nunca `throw exception;` (Microsoft, 2025a; Microsoft, 2026a).

Los recursos que implementen `IDisposable` se liberarán preferentemente mediante una declaración `using`. `finally` se reservará para limpieza imprescindible que no pueda expresarse mediante `using` (Microsoft, 2025a).

**Con estándar**

```csharp
public sealed class LoadGameService
{
    private readonly ISaveSerializer _saveSerializer;

    public LoadGameService(ISaveSerializer saveSerializer)
    {
        _saveSerializer = saveSerializer;
    }

    public SaveData LoadCheckpoint(string checkpointPath)
    {
        try
        {
            SaveData saveData = _saveSerializer.Read(checkpointPath);

            return saveData;
        }
        catch (FileNotFoundException exception)
        {
            throw new SaveGameException(
                "The checkpoint file was not found.",
                exception);
        }
        catch (IOException exception)
        {
            throw new SaveGameException(
                "The checkpoint file could not be read.",
                exception);
        }
    }
}
```

**Sin estándar**

```csharp
public sealed class LoadGameService
{
    public SaveData? LoadCheckpoint(string checkpointPath)
    {
        try
        {
            SaveData saveData = SaveSerializer.Read(checkpointPath);

            return saveData;
        }
        catch (Exception exception)
        {
            return null;
        }
    }
}
```

### 7.3 Null-checking (?., ??, tipos de referencia anulables)

El proyecto habilita los tipos de referencia anulables (\<Nullable>enable\</Nullable>). Un campo o parámetro de tipo referencia que legítimamente puede estar ausente se declara con ? (por ejemplo, WeaponData? equippedWeapon), y se accede mediante los operadores ?. y ?? en lugar de comprobaciones explícitas de if (x != null) cuando sea posible (Microsoft, 2024a).

Los tipos de referencia anulables permiten declarar qué variables pueden contener `null` y hacen que el compilador advierta cuando el uso del código no coincide con esa declaración, sin alterar el comportamiento en tiempo de ejecución. El contexto anulable se habilita mediante la opción `<Nullable>enable</Nullable>` del proyecto (Microsoft, 2024a).

**Con estándar**

```csharp
private const int DefaultAmmoCount = 0;

private WeaponData? _equippedWeapon;

private int GetEquippedAmmo()
{
    return _equippedWeapon?.AmmoCapacity ?? DefaultAmmoCount;
}
```

**Sin estándar**

```csharp
private const int DefaultAmmoCount = 0;

private WeaponData _equippedWeapon;

private int GetEquippedAmmo()
{
    int ammoCount;

    if (_equippedWeapon != null)
    {
        ammoCount = _equippedWeapon.AmmoCapacity;
    }
    else
    {
        ammoCount = DefaultAmmoCount;
    }

    return ammoCount;
}
```

### 7.4 Salidas anticipadas(early exit) en validaciones

Un método podrá retornar antes de completar su flujo normal cuando el objetivo sea evitar anidamiento innecesario al validar precondiciones (guard clauses), siguiendo el mismo principio de la regla 4.4 sobre claridad del código. Esta práctica no se adoptará por conveniencia del equipo, sino como una decisión arquitectónica orientada a mantener la complejidad ciclomática dentro del límite de la sección 8.2 y el anidamiento dentro del límite de la sección 8.5.

Cuando una salida anticipada no sea evidente por sí misma —por ejemplo, porque interrumpe un flujo que a primera vista parecería continuar, o porque responde a una regla de negocio específica del dominio del juego—, deberá acompañarse de un comentario de línea conforme a la regla 10.2, explicando la razón de la interrupción y no solo la condición evaluada (Martin, 2008; convención interna del equipo).

**Con estándar**

```csharp
public bool TryEquipWeapon(Player player, WeaponData weapon)
{
    if (!player.IsAlive)
    {
        return false;
    }

    if (player.Inventory.IsFull)
    {
        return false;
    }

    // A weapon above the player's level would be unusable until
    // leveling up, so equipping it early is rejected outright.
    if (weapon.RequiredLevel > player.Level)
    {
        return false;
    }

    player.Equip(weapon);

    return true;
}
```

**Sin estándar**

```csharp
public bool TryEquipWeapon(Player player, WeaponData weapon)
{
    bool wasEquipped = false;

    if (player.IsAlive)
    {
        if (!player.Inventory.IsFull)
        {
            if (weapon.RequiredLevel <= player.Level)
            {
                player.Equip(weapon);
                wasEquipped = true;
            }
        }
    }

    return wasEquipped;
}
```

## 8. Complejidad

La gestión de la complejidad en el código fuente es un pilar fundamental para asegurar la mantenibilidad, escalabilidad y la detección temprana de defectos en el desarrollo de software (Martin, 2008). En el contexto del desarrollo de videojuegos, donde los bucles lógicos se ejecutan decenas de veces por segundo, mantener una baja complejidad reduce drásticamente los cuellos de botella en el procesamiento y facilita la creación de pruebas unitarias efectivas.

### 8.1 Números mágicos

Se prohíbe el uso de literales numéricos distintos de `0`, `1` y `-1` cuando se usen como valores triviales de inicialización, incremento o comparación de signo directamente dentro de una expresión o instrucción. Todo valor numérico con significado de negocio, como umbrales de vida, cantidades de inventario, tiempos de aparición o identificadores de ranura, deberá declararse como una constante (`const`) o como un campo de solo lectura (`static readonly`) con un nombre descriptivo (Martin, 2008; convención interna del equipo para las excepciones `0`, `1` y `-1`).


**Con estándar**

```csharp
public class HealthSystem
{
    private const int LowHealthThreshold = 20;

    public bool IsLowHealth(int currentHealth)
    {
        return currentHealth <= LowHealthThreshold;
    }
}
```

**Sin estándar**

```csharp
public class HealthSystem
{
    public bool IsLowHealth(int currentHealth)
    {
        return currentHealth <= 20;
    }
}
```

### 8.2 Complejidad ciclomática máxima

Ningún método podrá superar una complejidad ciclomática de 10, medida como el número de caminos linealmente independientes en su grafo de flujo de control (McCabe, 1976; convención interna del equipo para el límite de 10). 

**Con estándar**

```csharp
public class CombatResolver
{
    private const int NoDamage = 0;
    private const int CriticalHitThreshold = 3;
    private const int CriticalDamageMultiplier = 2;

    public int ResolveAttack(Attacker attacker, Defender defender, WeaponData weapon)
    {
        int finalDamage = NoDamage;

        if (CanAttack(attacker, defender))
        {
            int baseDamage = CalculateBaseDamage(attacker, weapon);
            int reducedDamage = ApplyDefense(baseDamage, defender);
            finalDamage = ApplyCriticalModifier(reducedDamage, attacker.CriticalRolls);
        }

        return finalDamage;
    }

    private bool CanAttack(Attacker attacker, Defender defender)
    {
        bool canAttack = attacker.IsAlive
            && defender.IsAlive
            && attacker.HasStamina;

        return canAttack;
    }

    private int CalculateBaseDamage(Attacker attacker, WeaponData weapon)
    {
        int baseDamage = attacker.Strength * weapon.DamageMultiplier;

        return baseDamage;
    }

    private int ApplyDefense(int rawDamage, Defender defender)
    {
        int reducedDamage = rawDamage - defender.Armor;
        int finalDamage = Math.Max(reducedDamage, NoDamage);

        return finalDamage;
    }

    private int ApplyCriticalModifier(int damage, int criticalRolls)
    {
        int finalDamage = damage;

        if (criticalRolls >= CriticalHitThreshold)
        {
            finalDamage *= CriticalDamageMultiplier;
        }

        return finalDamage;
    }
}
```

**Sin estándar**

```csharp
public class CombatResolver
{
    public int ResolveAttack(Attacker attacker, Defender defender, WeaponData weapon)
    {
        int finalDamage = 0;
        if (attacker.IsAlive)
        {
            if (defender.IsAlive)
            {
                if (attacker.HasStamina)
                {
                    int rawDamage = attacker.Strength * weapon.DamageMultiplier;
                    if (rawDamage > 0)
                    {
                        int afterArmor = rawDamage - defender.Armor;
                        if (afterArmor < 0)
                        {
                            afterArmor = 0;
                        }
                        if (attacker.CriticalRolls >= 3)
                        {
                            if (defender.IsStunned)
                            {
                                finalDamage = afterArmor * 3;
                            }
                            else
                            {
                                finalDamage = afterArmor * 2;
                            }
                        }
                        else
                        {
                            finalDamage = afterArmor;
                        }
                    }
                }
            }
        }
        return finalDamage;
    }
}
```

### 8.3 Número máximo de parámetros por método

Todo método podrá recibir como máximo tres parámetros. Cuando la operación requiera más datos de entrada, estos deberán agruparse en un tipo dedicado (struct o class según corresponda por la sección 10.7 de este estándar), en lugar de ampliar la firma del método (McConnell, 2004; convención interna del equipo para el máximo de tres parámetros).

 McConnell (2004) reporta que las firmas de método extensas dificultan tanto la lectura en el punto de llamada como la comprobación del orden correcto de los argumentos, y recomienda agrupar parámetros relacionados en un objeto propio cuando su número crece. 

**Con estándar**

```csharp
public Enemy Spawn(EnemySpawnRequest request)
{
    Enemy enemy = enemyFactory.Create(request.Type, request.Position);
    enemy.Configure(request.Level, request.Faction);
    return enemy;
}
```

**Sin estándar**

```csharp
public Enemy Spawn(EnemyType type, float positionX, float positionY, float positionZ, int level, Faction faction)
{
    Enemy enemy = enemyFactory.Create(type, positionX, positionY, positionZ);
    enemy.Configure(level, faction);
    return enemy;
}
```

### 8.4 Número máximo de operadores lógicos por expresión

Ninguna expresión condicional podrá contener más de tres operadores lógicos o de comparación (&&, ||, ==, !=, <, >, <=, >=) combinados en una misma línea. Cuando una condición requiera evaluar más criterios, estos deberán descomponerse en variables booleanas intermedias con nombre descriptivo (McCabe, 1976; Martin, 2008; convención interna del equipo para el máximo de tres operadores).

**Con estándar**

```csharp
public class SaveSystem
{
    private const int MinimumProgressPercent = 5;

    public bool CanSaveGame(PlayerState state, LevelState level)
    {
        bool hasMinimumProgress = level.ProgressPercent >= MinimumProgressPercent;
        bool isInSafeZone = level.CurrentZone.IsSafe;
        bool isPlayerAlive = state.IsAlive;
        bool isNotInCutscene = !level.IsPlayingCutscene;

        return hasMinimumProgress && isInSafeZone && isPlayerAlive && isNotInCutscene;
    }
}
```

**Sin estándar**

```csharp
public class SaveSystem
{
    public bool CanSaveGame(PlayerState state, LevelState level)
    {
        return level.ProgressPercent >= 5 && level.CurrentZone.IsSafe && state.IsAlive && !level.IsPlayingCutscene && state.Stamina > 0;
    }
}
```

### 8.5 Máximo de niveles de anidamiento

Ningún bloque de código podrá anidarse más de tres niveles de profundidad dentro de un mismo método, contando estructuras de control (`if`, `for`, `foreach`, `while`, `switch`) y bloques `try`. Cuando una operación requiera un nivel adicional, se extraerá a un método privado con nombre descriptivo, o se aplicará una salida anticipada conforme a la regla 7.4 (McCabe, 1976; Martin, 2008; convención interna del equipo para el límite de tres niveles).

**Con estándar**

```csharp
public void ApplyAreaDamage(IEnumerable<Enemy> enemies, int damage)
{
    foreach (Enemy enemy in enemies)
    {
        if (!enemy.IsAlive)
        {
            continue;
        }

        ApplyDamageIfInRange(enemy, damage);
    }
}

private void ApplyDamageIfInRange(Enemy enemy, int damage)
{
    if (enemy.IsInRange)
    {
        enemy.ReceiveDamage(damage);
    }
}
```

**Sin estándar**

```csharp
public void ApplyAreaDamage(IEnumerable<Enemy> enemies, int damage)
{
    foreach (Enemy enemy in enemies)
    {
        if (enemy.IsAlive)
        {
            if (enemy.IsInRange)
            {
                if (damage > 0)
                {
                    enemy.ReceiveDamage(damage);
                }
            }
        }
    }
}
```


## 9. Prácticas específicas de C#

### 9.1 Propiedades vs. campos públicos

### 9.2 Uso de LINQ (restricciones en rutas de ejecución frecuentes)

### 9.3 Reutilización de referencias y Object Pooling

### 9.4 Objetos para datos y configuración

### 9.5 Serialización (`[System.Serializable]` y serializador seleccionado)

### 9.6 Eventos (`event`, `EventHandler` y `Action`)

### 9.7 Structs vs. classes vs. records (posiciones, stats, DTOs de guardado)

Se utilizará record (o record struct) cuando el tipo represente datos inmutables cuya igualdad deba compararse por valor: DTOs de guardado, mensajes de red, y snapshots de estado enviados entre sistemas. Se utilizará class cuando el tipo tenga identidad propia, comportamiento con efectos secundarios, o un ciclo de vida mutable gestionado por el propio sistema de juego (entidades como Player o Enemy). Se utilizará struct únicamente para datos pequeños, inmutables y de alta frecuencia de creación donde el costo de asignación en el heap sea relevante, como vectores o posiciones (Microsoft, s. f.-f; convención interna del equipo).

**Con estándar**

```csharp
public sealed record SaveGameDto(
    string PlayerName,
    int CurrentHealth,
    int Level);

public sealed class Player
{
    public int CurrentHealth { get; private set; }

    public void ReceiveDamage(int amount)
    {
        CurrentHealth -= amount;
    }
}
```

**Sin estándar**

```csharp
public sealed class SaveGameDto
{
    public string PlayerName { get; set; }
    public int CurrentHealth { get; set; }
    public int Level { get; set; }
}
```

## 10. Comentarios y documentación

Todo fragmento de código que se desvíe de una norma del estándar, que implemente una decisión de diseño no evidente o que resuelva un caso especial deberá estar acompañado de un comentario que explique el motivo de dicha decisión, no únicamente lo que hace el código. Los comentarios se escriben en inglés, por consistencia con el resto del código fuente (Microsoft, 2025d; Martin, 2008).

### 10.1 Comentarios de bloque

Los comentarios de bloque (`/* ... */`) se utilizarán de manera excepcional cuando una justificación necesite conservarse como un bloque breve de varias líneas. Se colocarán antes del código al que se refieren, precedidos por una línea en blanco y al mismo nivel de indentación. Cuando una sola línea sea suficiente, se utilizará el formato `//` definido en 10.2 (Microsoft, 2025d; convención interna del equipo sobre comentarios de bloque).

Los comentarios de bloque nunca deberán utilizarse para construir separadores decorativos mediante líneas de asteriscos (Microsoft, 2025d; convención interna del equipo).

Las convenciones de Microsoft utilizan comentarios `//` para explicaciones breves y desaconsejan los comentarios de bloque para explicaciones extensas. Por ello, `/* ... */` se mantiene como una excepción limitada del equipo y nunca se utilizará como separador decorativo (Microsoft, 2025d).

**Con estándar**

```csharp
/*
The field order is preserved because existing save files use positional serialization.
Changing it would make saved games unreadable.
*/
_saveSerializer.Write(saveData);
```

**Sin estándar**

```csharp
/****************************************
 * SAVE SECTION
 ****************************************/
_saveSerializer.Write(saveData);
```

### 10.2 Comentarios de línea

Los comentarios de una sola línea (`//`) inician con mayúscula, terminan con punto y llevan un espacio entre `//` y el texto. Se colocan en su propia línea, precedidos por una línea en blanco cuando aportan claridad; no se colocan al final de una línea de código (Microsoft, 2025d).

Los comentarios de línea constituyen el formato habitual para justificar decisiones no evidentes. La convención oficial de C# indica que el comentario se coloca en una línea separada, inicia con mayúscula, termina con punto y lleva un espacio después del delimitador (Microsoft, 2025d).

**Con estándar**

```csharp
private const int MinimumHealth = 0;

// Skip regeneration once the player has already been defeated.
if (_currentHealth > MinimumHealth)
{
    RegenerateHealth();
}
```

**Sin estándar**

```csharp
private const int MinimumHealth = 0;

if (_currentHealth > MinimumHealth) // skip regeneration once the player has already been defeated
{
    RegenerateHealth();
}
```

### 10.3 Comentarios de documentación XML (///)

La documentación XML (`///`) se utilizará únicamente en las clases de servicio, las interfaces públicas de servicio y sus miembros públicos. Las entidades, objetos de valor, componentes internos y clases de prueba no deberán documentarse con XML salvo que formen parte de un contrato público. Esta delimitación es una decisión del equipo para evitar documentación repetitiva en miembros cuyo propósito ya es evidente (Microsoft, 2026e; convención interna del equipo sobre el alcance de la documentación).

Todo servicio público deberá incluir como mínimo `<summary>`. Cada miembro documentado agregará las etiquetas que correspondan a su firma y comportamiento. El texto deberá escribirse en inglés, con oraciones completas, y colocarse inmediatamente antes del elemento, sin una línea en blanco. La documentación deberá ser XML bien formado (Microsoft, 2026e).

Los ejemplos de este estándar podrán omitir la documentación XML cuando estén demostrando una regla diferente. Esta excepción editorial evita llenar los ejemplos con información ajena al punto evaluado; no se aplicará al código de producción (Microsoft, 2026e; convención editorial interna del equipo).

Las etiquetas oficiales se utilizarán de la siguiente manera (Microsoft, 2026e):

| Etiqueta o atributo | Uso |
| --- | --- |
| `<summary>` | Resume la responsabilidad del tipo o miembro. Es obligatorio en los servicios documentados. |
| `<remarks>` | Agrega condiciones de uso o detalles que no pertenecen al resumen. |
| `<param>` | Describe cada parámetro de un método o constructor. |
| `<paramref>` | Hace referencia a un parámetro dentro de otra etiqueta. |
| `<returns>` | Describe el valor devuelto por un método no `void`. |
| `<value>` | Describe el valor que representa una propiedad. |
| `<exception>` | Indica cada excepción que el miembro puede lanzar directamente y la condición que la provoca. |
| `<typeparam>` | Describe cada parámetro de tipo genérico. |
| `<typeparamref>` | Hace referencia a un parámetro de tipo dentro del texto. |
| `<see>` | Crea una referencia en línea a otro miembro, tipo, palabra clave o vínculo. |
| `<seealso>` | Agrega una referencia relacionada al final de la documentación. |
| `cref` | Identifica un tipo o miembro de código y permite que el compilador valide la referencia. |
| `href` | Identifica un vínculo externo cuando la referencia no es un elemento de código. |
| `<example>` | Presenta un ejemplo de uso cuando el contrato no resulte evidente. |
| `<c>` | Marca como código un fragmento corto dentro de una oración. |
| `<code>` | Contiene un ejemplo de código de varias líneas. |
| `<para>` | Divide una explicación extensa en párrafos. |
| `<list>` | Presenta una lista o tabla dentro de la documentación generada. |
| `<inheritdoc>` | Hereda documentación de una interfaz, clase base o miembro equivalente. |
| `<include>` | Reutiliza documentación almacenada en un archivo XML externo. |
| `<b>`, `<i>`, `<u>`, `<br/>` y `<a>` | Aplican formato básico; se utilizarán solo cuando mejoren la comprensión. |
| `<safety>` | Documenta obligaciones de código `unsafe`; no se utilizará mientras el proyecto prohíba código `unsafe`. |

No se utilizará `<tt>` porque es una etiqueta obsoleta; para código en línea se utilizará `<c>`. Microsoft reconoce las etiquetas anteriores para los escenarios habituales de documentación y valida de forma especial elementos como `<param>`, `<exception>`, `<see>`, `<seealso>`, `<typeparam>` e `<include>` (Microsoft, 2026e).

**Con estándar**

```csharp
/// <summary>
/// Provides operations for storing the current game state.
/// </summary>
public sealed class SaveGameService
{
    private const int MinimumSlot = 1;
    private const int MaximumSlot = 3;

    private readonly ISaveGameRepository _saveGameRepository;

    /// <summary>
    /// Initializes a service with the repository used to store game states.
    /// </summary>
    /// <param name="saveGameRepository">The repository used for persistence.</param>
    /// <exception cref="ArgumentNullException">
    /// Thrown when <paramref name="saveGameRepository"/> is null.
    /// </exception>
    public SaveGameService(ISaveGameRepository saveGameRepository)
    {
        ArgumentNullException.ThrowIfNull(saveGameRepository);
        _saveGameRepository = saveGameRepository;
    }

    /// <summary>
    /// Stores the supplied player state in the selected slot.
    /// </summary>
    /// <param name="playerState">The player state to store.</param>
    /// <param name="slot">The destination save slot.</param>
    /// <returns>The result reported by the save repository.</returns>
    /// <exception cref="ArgumentNullException">
    /// Thrown when <paramref name="playerState"/> is null.
    /// </exception>
    /// <exception cref="ArgumentOutOfRangeException">
    /// Thrown when <paramref name="slot"/> is outside the supported range.
    /// </exception>
    public SaveResult Save(PlayerState playerState, int slot)
    {
        ArgumentNullException.ThrowIfNull(playerState);

        if (slot < MinimumSlot || slot > MaximumSlot)
        {
            throw new ArgumentOutOfRangeException(nameof(slot));
        }

        SaveResult saveResult = _saveGameRepository.Save(playerState, slot);

        return saveResult;
    }
}
```

**Sin estándar**

```csharp
/// <summary>
/// Saves data.
/// </summary>
public sealed class SaveGameService
{
    public SaveResult Save(PlayerState playerState, int slot)
    {
        SaveResult saveResult = SaveRepository.Save(playerState, slot);

        return saveResult;
    }
}
```

### 10.4 Comentarios especiales (TODO, FIXME)

`TODO` marca funcionalidad pendiente de implementar; `FIXME` marca un comportamiento incorrecto conocido que debe corregirse. Ambos se escriben en mayúsculas, se colocan inmediatamente antes de la sección de código correspondiente, y deben ir acompañados de una descripción clara del pendiente. Todo comentario `TODO` o `FIXME` debe resolverse antes de la entrega final (Microsoft, 2025d; convención interna del equipo).

El reconocimiento automático de estos tokens dependerá del editor utilizado. La obligación de resolverlos antes de la entrega se mantiene independientemente de que el editor los muestre en una lista de tareas (Microsoft, 2025d; convención interna del equipo).

**Con estándar**

```csharp
// TODO: Add a cooldown so this ability cannot be reused every frame.
ActivateSpecialAbility();
```

**Sin estándar**

```csharp
// todo fix
ActivateSpecialAbility();
```

## 11. Manejo de logs y categorización de errores

El registro de eventos (logging) es el mecanismo principal para diagnosticar el comportamiento de un videojuego una vez que ya no se está depurando paso a paso dentro del editor, especialmente en sistemas que se ejecutan por frame (spawn de enemigos, resolución de combate) o que involucran persistencia (guardado de partida). Esta sección regula la herramienta de logging a utilizar, los niveles disponibles, el criterio para elegir cada nivel, el formato del mensaje y la diferencia de comportamiento entre el editor y el build final (Chuvakin et al., 2013).

### 11.1 Sistema/herramienta de logging

El proyecto utilizará `log4net` como biblioteca de logging. Debido a que el estándar también exige el nivel `Trace`, se utilizará la extensión oficial `log4net.Ext.Trace`, la cual agrega `ITraceLog` y `TraceLogManager` sobre los niveles principales de `log4net` (Apache Logging Services, s. f.-a, s. f.-b).

Cada clase que necesite registrar eventos declarará un único logger privado, estático y de solo lectura. El campo se llamará `_logger`, de acuerdo con la regla 4.5, sin utilizar el prefijo `s_`. Queda prohibido utilizar `Console.WriteLine`, `Debug.WriteLine` o crear un sistema de niveles paralelo a `log4net`. Apache documenta `log4net.Ext.Trace` como la extensión que añade el nivel `Trace` y define `Debug`, `Info`, `Warn`, `Error` y `Fatal` como los niveles principales de `ILog` (Apache Logging Services, s. f.-a, s. f.-b).

**Con estándar**

```csharp
using log4net.Ext.Trace;

public sealed class SaveGameService
{
    private static readonly ITraceLog _logger =
        TraceLogManager.GetLogger(typeof(SaveGameService));

    private readonly ISaveGameRepository _saveGameRepository;

    public SaveGameService(ISaveGameRepository saveGameRepository)
    {
        _saveGameRepository = saveGameRepository;
    }

    public void SaveGame(PlayerState playerState)
    {
        _logger.Info("Game save started.");
        _saveGameRepository.Save(playerState);
    }
}
```

**Sin estándar**

```csharp
public sealed class SaveGameService
{
    private readonly ISaveGameRepository _saveGameRepository;

    public SaveGameService(ISaveGameRepository saveGameRepository)
    {
        _saveGameRepository = saveGameRepository;
    }

    public void SaveGame(PlayerState playerState)
    {
        Console.WriteLine("Game save started.");
        _saveGameRepository.Save(playerState);
    }
}
```

### 11.2 Niveles de log: Trace, Debug, Info, Warn, Error y Fatal

Se utilizarán seis niveles, ordenados de menor a mayor severidad: `Trace`, `Debug`, `Info`, `Warn`, `Error` y `Fatal`. En el código se escribirá `Warn`, no `Warning`, porque ese es el nombre del método expuesto por `log4net`. Los niveles `All` y `Off` se reservarán para configuración y filtrado; no se utilizarán para registrar eventos (Apache Logging Services, s. f.-a, s. f.-b).

La documentación de Apache establece el orden `Debug < Info < Warn < Error < Fatal`; `Trace` se incorpora por debajo de `Debug` mediante la extensión oficial (Apache Logging Services, s. f.-a, s. f.-b).

**Con estándar**

```csharp
_logger.Trace("Enemy position updated.");
_logger.Debug("Damage modifiers calculated.");
_logger.Info("Game saved successfully.");
_logger.Warn("Save file version is outdated.");
_logger.Error("The save operation failed.");
_logger.Fatal("The game state cannot be initialized.");
```

**Sin estándar**

```csharp
Console.WriteLine("Something happened.");
```

### 11.3 Criterio de aplicación por nivel (contexto de juego)

Cada nivel deberá reservarse para el siguiente tipo de evento (Apache Logging Services, s. f.-a, s. f.-b; Chuvakin et al., 2013):

- `Trace`: eventos de muy alta frecuencia usados solo para depuración fina (posición del jugador en cada ciclo de actualización, cada iteración de un bucle de física).
- `Debug`: información de desarrollo no crítica (valores intermedios de una fórmula de daño, estado de una máquina de estados de un enemigo).
- `Info`: hitos normales del flujo del juego (partida guardada correctamente, jugador entra a un nuevo nivel, enemigo generado por `EnemySpawner`).
- `Warn`: situaciones anómalas pero recuperables (intento de recoger un objeto con el inventario lleno, archivo de guardado con una versión antigua pero migrable).
- `Error`: fallos que impiden completar una operación, pero permiten que la aplicación o el subsistema continúen (fallo de escritura de una partida o pérdida temporal de conexión).
- `Fatal`: fallos irrecuperables que impiden que la aplicación o un subsistema esencial continúen de forma segura (configuración principal inválida, corrupción del estado inicial o imposibilidad de iniciar los servicios esenciales).

**Con estándar**

```csharp
public sealed class InventoryService
{
    private const int MaximumSlots = 20;

    private static readonly ITraceLog _logger =
        TraceLogManager.GetLogger(typeof(InventoryService));

    public bool AddItem(ICollection<Item> items, Item item)
    {
        bool wasAdded = false;

        if (items.Count >= MaximumSlots)
        {
            _logger.Warn("The inventory is full; the item was not added.");
        }
        else
        {
            items.Add(item);
            wasAdded = true;
        }

        return wasAdded;
    }
}
```

**Sin estándar**

```csharp
if (items.Count >= MaximumSlots)
{
    _logger.Error("The inventory is full.");
    return false;
}
```

### 11.4 Formato del mensaje

Los mensajes se escribirán en inglés, iniciarán con mayúscula y terminarán con punto. Deberán describir un evento específico e incluir el contexto mínimo necesario para diagnosticarlo. El nombre del logger identificará la clase de origen, por lo que no se repetirá manualmente como categoría dentro del mensaje (Apache Logging Services, s. f.-b; Chuvakin et al., 2013).

Los valores dinámicos se enviarán mediante los métodos terminados en `Format`, como `InfoFormat`, en vez de concatenar cadenas. Cuando se registre una excepción se utilizará la sobrecarga que recibe el mensaje y el objeto `Exception`, para conservar la traza. No se registrarán contraseñas, tokens, datos personales ni contenido completo de archivos de guardado (Apache Logging Services, s. f.-b; Chuvakin et al., 2013).

**Con estándar**

```csharp
_logger.InfoFormat(
    "Enemy spawned. Type: {0}.",
    request.Type);

_logger.Error(
    "The checkpoint file could not be written.",
    exception);
```

**Sin estándar**

```csharp
_logger.Info("Enemy spawned: " + request.Type.ToString());
```

### 11.5 Logs en entornos de desarrollo y versiones finales

Los niveles `Trace` y `Debug` se habilitarán únicamente en configuraciones de desarrollo. En las versiones finales, el umbral se configurará como mínimo en `Info`. Los niveles `Info`, `Warn`, `Error` y `Fatal` permanecerán disponibles en la versión final, y cada appender podrá aplicar un umbral más alto según su destino (Apache Logging Services, s. f.-b; Chuvakin et al., 2013).

El filtrado se realizará en la configuración de `log4net`; no se agregarán condicionales de compilación o comprobaciones manuales alrededor de cada llamada. `log4net` habilita una solicitud cuando su nivel es igual o superior al umbral efectivo del logger (Apache Logging Services, s. f.-b).

**Con estándar**

```xml
<root>
  <level value="INFO" />
  <appender-ref ref="RollingFileAppender" />
</root>
```

**Sin estándar**

```xml
<root>
  <level value="DEBUG" />
  <appender-ref ref="RollingFileAppender" />
</root>
```

### 11.6 Criterio para loggear una excepción

No toda excepción capturada se registrará en el punto donde se captura. Una excepción se registrará únicamente en el punto donde se resuelve de forma definitiva dentro de la pila de llamadas: donde se maneja sin relanzarla, o donde se captura en el límite superior de la aplicación conforme a la regla 7.2. Si un bloque `catch` relanza la excepción mediante `throw`; o la envuelve en una excepción de dominio conservando la excepción original en `InnerException`, ese punto no registrará el evento, ya que el registro corresponde al nivel donde el flujo finalmente se detiene o se recupera. Esto evita que un mismo fallo aparezca duplicado en varios niveles de la pila, lo cual dificulta la auditoría en lugar de facilitarla.

El nivel del registro se seleccionará con los criterios ya definidos en la sección 11.3: `Warn` si la operación se degrada pero el sistema continúa sin intervención del jugador, `Error` si la operación falla y afecta al jugador pero la aplicación permanece estable, y `Fatal` si compromete la continuidad segura de la aplicación. Un `catch` que maneje una condición esperada del flujo normal del juego no constituye una excepción registrable en este nivel de severidad, en congruencia con la regla 7.1, que reserva las excepciones para condiciones verdaderamente excepcionales.(Microsoft, 2025a; Microsoft, 2026a).

**Con estándar**

```xml

public sealed class GameBootstrapper
{
    private static readonly ITraceLog _logger =
        TraceLogManager.GetLogger(typeof(GameBootstrapper));

    private readonly LoadGameService _loadGameService;

    public GameBootstrapper(LoadGameService loadGameService)
    {
        _loadGameService = loadGameService;
    }

    public void StartGame(string checkpointPath)
    {
        try
        {
            SaveData saveData = _loadGameService.LoadCheckpoint(checkpointPath);
        }
        catch (SaveGameException exception)
        {
            _logger.Error(
                "The game could not start from the checkpoint.",
                exception);
        }
    }
}
```

**Sin estándar**

```xml

public sealed class LoadGameService
{
    private static readonly ITraceLog _logger =
        TraceLogManager.GetLogger(typeof(LoadGameService));

    private readonly ISaveSerializer _saveSerializer;

    public LoadGameService(ISaveSerializer saveSerializer)
    {
        _saveSerializer = saveSerializer;
    }

    public SaveData LoadCheckpoint(string checkpointPath)
    {
        try
        {
            return _saveSerializer.Read(checkpointPath);
        }
        catch (IOException exception)
        {
            _logger.Error(
                "The checkpoint file could not be read.",
                exception);

            throw new SaveGameException(
                "The checkpoint file could not be read.",
                exception);
        }
    }
}
```

## 12. Gestión de estados, pantallas y UI

### 12.1 Navegación centralizada entre estados o pantallas

### 12.2 Mensajes/feedback al jugador (HUD, popups, pantallas de carga)

### 12.3 Recursos de traducción y textos centralizados

Todo texto visible para el jugador (diálogos, etiquetas de UI, mensajes de error mostrados en pantalla) se almacenará en archivos de recursos (.resx) organizados por idioma, y se accederá mediante una clase de recursos generada automáticamente, nunca mediante cadenas de texto escritas directamente en el código de UI. Esto permite cambiar el idioma del juego sin recompilar ni modificar lógica, conforme al soporte español/inglés previsto para el proyecto (Microsoft, s. f.-h; convención interna del equipo).

Los mensajes de log (sección 11) y las excepciones (sección 7) no se traducirán y permanecerán en inglés, ya que están dirigidos al equipo de desarrollo, no al jugador; esta regla aplica exclusivamente a texto dirigido al usuario final.

**Con estándar**

```csharp

public sealed class MainMenuView
{
    public string GetPlayButtonLabel()
    {
        return UiStrings.PlayButtonLabel;
    }
}
```

**Sin estándar**

```csharp

public sealed class MainMenuView
{
    public string GetPlayButtonLabel()
    {
        return "Jugar";
    }
}
```

## 13. Validación de entradas y seguridad

### 13.1 Validación de inputs del jugador

### 13.2 Autoridad del servidor (si el proyecto es multijugador)

### 13.3 Manejo de datos sensibles

### 13.4 Persistencia de partidas (save/load) e integridad de datos

## 14. Pruebas unitarias

Las pruebas unitarias deberán verificar comportamientos individuales del código de manera rápida, aislada, repetible y automática. No deberán depender de archivos reales, conexiones externas, servicios remotos, fechas del sistema ni otros recursos que puedan producir resultados variables (Microsoft, 2025b).

Las pruebas se escribirán utilizando NUnit como framework de referencia. Las dependencias deberan sustituirse mediante NSubstitute (Microsoft, 2025b; NUnit Project, s. f.-c; NSubstitute, s. f.).

Estas reglas se basan en las prácticas recomendadas para pruebas unitarias de .NET y en la documentación oficial de NUnit (Microsoft, 2025b; NUnit Project, s. f.-c).

### 14.1 Framework y ubicación (Unit / Integration)

**Framework de pruebas**

Las pruebas se escribirán utilizando NUnit. Por convención del equipo, las clases de prueba utilizarán `[TestFixture]`, aunque NUnit permite omitirlo en clases no genéricas y no parametrizadas. Los métodos sin parámetros deberán marcarse con `[Test]`; los métodos parametrizados deberán utilizar `[TestCase]` o `[TestCaseSource]` (NUnit Project, s. f.-c, s. f.-d, s. f.-e).

**Con estándar**

```csharp
using NUnit.Framework;

[TestFixture]
public sealed class DamageCalculatorTests
{
    [Test]
    public void Test_CalculateDamage_AttackExceedsDefense_ReturnsDamageAfterDefense()
    {
        const int AttackPower = 30;
        const int Defense = 10;
        const int ExpectedDamage = 20;
        DamageCalculator damageCalculator = new DamageCalculator();

        int actualDamage = damageCalculator.CalculateDamage(
            AttackPower,
            Defense);

        Assert.That(actualDamage, Is.EqualTo(ExpectedDamage));
    }
}
```

**Sin estándar**

```csharp
public sealed class DamageCalculatorTests
{
    public bool CheckDamage()
    {
        DamageCalculator damageCalculator = new DamageCalculator();
        return damageCalculator.CalculateDamage(30, 10) == 20;
    }
}
```

**Separación entre pruebas unitarias y de integración**

Las pruebas unitarias y las pruebas de integración deberán almacenarse en proyectos o ensamblados separados (Microsoft, 2025b; convención interna del equipo).

Las pruebas unitarias se colocarán en `tests/AdventureGame.Tests.Unit`. Las pruebas de integración se colocarán en `tests/AdventureGame.Tests.Integration` (Microsoft, 2025b; convención interna del equipo para las rutas).

**Con estándar**

```csharp
tests/AdventureGame.Tests.Unit/Combat/DamageCalculatorTests.cs
tests/AdventureGame.Tests.Unit/Characters/PlayerTests.cs
tests/AdventureGame.Tests.Integration/Saving/SaveGameRepositoryTests.cs
```

**Sin estándar**

```csharp
tests/Tests/DamageCalculatorTests.cs
tests/Tests/PlayerTests.cs
tests/Tests/SaveGameRepositoryTests.cs
```

**Ubicación de pruebas unitarias**

Las clases que prueben lógica aislada, cálculos, validaciones, reglas de combate o transformaciones de datos deberán colocarse dentro del proyecto de pruebas unitarias (Microsoft, 2025b).

**Con estándar**

```csharp
tests/AdventureGame.Tests.Unit/Combat/DamageCalculatorTests.cs
```

**Sin estándar**

```csharp
tests/AdventureGame.Tests.Integration/Combat/DamageCalculatorTests.cs
```

**Ubicación de pruebas de integración**

Las pruebas que utilicen archivos reales, bases de datos, servicios externos o varios componentes concretos deberán colocarse dentro del proyecto de pruebas de integración (Microsoft, 2025b).

**Con estándar**

```csharp
tests/AdventureGame.Tests.Integration/Saving/FileSaveGameRepositoryTests.cs
```

**Sin estándar**

```csharp
tests/AdventureGame.Tests.Unit/Saving/FileSaveGameRepositoryTests.cs
```

**Correspondencia entre archivos y clases de prueba**

Cada archivo deberá contener una sola clase de prueba. El nombre del archivo deberá coincidir con el nombre de la clase (Microsoft, 2025b; Microsoft, 2025d; convención interna del equipo).

**Con estándar — archivo `PlayerTests.cs`**

```csharp
[TestFixture]
public sealed class PlayerTests
{
}
```

**Sin estándar — archivo `Tests.cs`**

```csharp
[TestFixture]
public sealed class PlayerTests
{
}

[TestFixture]
public sealed class EnemyTests
{
}
```

**Pruebas parametrizadas**

Cuando el mismo comportamiento deba comprobarse con diferentes entradas, se utilizará `[TestCase]` en lugar de duplicar métodos. Cada ejecución parametrizada conservará un solo assert. El atributo `[TestCase]` identifica por sí mismo el método como una prueba parametrizada; no será necesario agregar `[Test]` al mismo método (NUnit Project, s. f.-d).

**Con estándar**

```csharp
[TestCase(30, 10, 20)]
[TestCase(30, 20, 10)]
[TestCase(30, 30, 0)]
public void Test_CalculateDamage_DifferentDefense_ReturnsExpectedDamage(
    int attackPower,
    int defense,
    int expectedDamage)
{
    DamageCalculator damageCalculator = new DamageCalculator();

    int actualDamage = damageCalculator.CalculateDamage(
        attackPower,
        defense);

    Assert.That(actualDamage, Is.EqualTo(expectedDamage));
}
```

**Sin estándar**

```csharp
[Test]
public void Test_CalculateDamage_DifferentValues_ReturnsSomething()
{
    DamageCalculator damageCalculator = new DamageCalculator();

    int firstDamage = damageCalculator.CalculateDamage(30, 10);
    int secondDamage = damageCalculator.CalculateDamage(30, 20);

    Assert.That(firstDamage, Is.EqualTo(20));
    Assert.That(secondDamage, Is.EqualTo(10));
}
```

### 14.2 Estructura Arrange-Act-Assert

Cada prueba deberá seguir el patrón Arrange-Act-Assert (Microsoft, 2025b):

1. **Arrange:** crea y configura los datos, dependencias y objeto probado.
2. **Act:** ejecuta una sola operación sobre el objeto probado.
3. **Assert:** comprueba un único resultado observable.

Las tres etapas deberán separarse mediante una línea en blanco. No será necesario agregar comentarios `// Arrange`, `// Act` y `// Assert` cuando la separación y los nombres hagan evidente la estructura (Microsoft, 2025b).

**Con estándar**

```csharp
[Test]
public void Test_CalculateDamage_EnemyHasDefense_ReturnsReducedDamage()
{
    const int AttackPower = 30;
    const int Defense = 10;
    const int ExpectedDamage = 20;
    DamageCalculator damageCalculator = new DamageCalculator();

    int actualDamage = damageCalculator.CalculateDamage(
        AttackPower,
        Defense);

    Assert.That(actualDamage, Is.EqualTo(ExpectedDamage));
}
```

**Sin estándar**

```csharp
[Test]
public void Test_CalculateDamage_EnemyHasDefense_ReturnsReducedDamage()
{
    Assert.That(
        new DamageCalculator().CalculateDamage(30, 10),
        Is.EqualTo(20));
}
```

**Contenido de Arrange**

La etapa Arrange deberá contener únicamente la creación y configuración necesarias para el comportamiento probado. No se configurarán propiedades o dependencias que no influyan en el resultado (Microsoft, 2025b).

**Con estándar**

```csharp
[Test]
public void Test_IsAlive_HealthIsPositive_ReturnsTrue()
{
    Player player = new PlayerBuilder()
        .WithHealth(InitialHealth)
        .Build();

    bool isAlive = player.IsAlive;

    Assert.That(isAlive, Is.True);
}
```

**Sin estándar**

```csharp
[Test]
public void Test_IsAlive_HealthIsPositive_ReturnsTrue()
{
    Player player = new PlayerBuilder()
        .WithHealth(InitialHealth)
        .WithName("Player")
        .WithLevel(10)
        .WithExperience(500)
        .WithGold(1000)
        .Build();

    bool isAlive = player.IsAlive;

    Assert.That(isAlive, Is.True);
}
```

**Una operación en Act**

La etapa Act deberá contener una sola operación principal. Si una prueba necesita ejecutar varias acciones independientes, deberá dividirse en pruebas separadas (Microsoft, 2025b).

**Con estándar**

```csharp
[Test]
public void Test_ReceiveDamage_DamageIsPositive_ReducesHealth()
{
    Player player = new PlayerBuilder()
        .WithHealth(InitialHealth)
        .Build();

    player.ReceiveDamage(ReceivedDamage);

    Assert.That(player.Health, Is.EqualTo(ExpectedHealth));
}
```

**Sin estándar**

```csharp
[Test]
public void Test_PlayerActions_ValidValues_UpdatePlayer()
{
    Player player = new PlayerBuilder().Build();

    player.ReceiveDamage(ReceivedDamage);
    player.RestoreHealth();
    player.AddExperience(EarnedExperience);

    Assert.That(player.Health, Is.EqualTo(ExpectedHealth));
}
```

**Separación de Act y Assert**

La operación probada no deberá ejecutarse directamente dentro del assert. Su resultado deberá almacenarse en una variable con un nombre descriptivo (Microsoft, 2025b).

**Con estándar**

```csharp
[Test]
public void Test_GetAttackPower_PlayerHasWeapon_ReturnsTotalAttackPower()
{
    Player player = new PlayerBuilder()
        .WithWeapon(defaultWeapon)
        .Build();

    int actualAttackPower = player.GetAttackPower();

    Assert.That(actualAttackPower, Is.EqualTo(ExpectedAttackPower));
}
```

**Sin estándar**

```csharp
[Test]
public void Test_GetAttackPower_PlayerHasWeapon_ReturnsTotalAttackPower()
{
    Player player = new PlayerBuilder()
        .WithWeapon(defaultWeapon)
        .Build();

    Assert.That(
        player.GetAttackPower(),
        Is.EqualTo(ExpectedAttackPower));
}
```

Cuando se pruebe una excepción, la operación se representará mediante un delegado creado en la etapa Act. `Assert.Throws` ejecutará ese delegado durante la etapa Assert. Esta es una excepción intencional a la separación estricta entre Act y Assert, porque la comprobación requiere observar la excepción producida al ejecutar el delegado (NUnit Project, s. f.-a).

### 14.3 Un assert por test

Cada prueba deberá contener un solo assert. Esta es una política del equipo que busca que cada método verifique un único comportamiento y permita identificar con precisión la causa de un fallo. NUnit recomienda intentar mantener un assert por prueba, aunque el framework también admite la agrupación de varias comprobaciones (NUnit Project, s. f.-b).

Una verificación de NSubstitute mediante `Received()` contará como el único assert de la prueba (NSubstitute, s. f.; convención interna del equipo).

**Con estándar**

```csharp
[Test]
public void Test_ReceiveDamage_DamageIsPositive_ReducesHealth()
{
    Player player = new PlayerBuilder()
        .WithHealth(InitialHealth)
        .Build();

    player.ReceiveDamage(ReceivedDamage);

    Assert.That(player.Health, Is.EqualTo(ExpectedHealth));
}
```

**Sin estándar**

```csharp
[Test]
public void Test_ReceiveDamage_ValidDamage_UpdatesPlayer()
{
    Player player = new PlayerBuilder()
        .WithHealth(InitialHealth)
        .Build();

    player.ReceiveDamage(ReceivedDamage);

    Assert.That(player.Health, Is.EqualTo(ExpectedHealth));
    Assert.That(player.IsAlive, Is.True);
}
```

**Separación de comportamientos**

Si una operación produce varios resultados que deben comprobarse por separado, se escribirá una prueba para cada comportamiento (Microsoft, 2025b; NUnit Project, s. f.-b).

**Con estándar**

```csharp
[Test]
public void Test_ReceiveFatalDamage_DamageExceedsHealth_SetsIsAliveToFalse()
{
    Player player = new PlayerBuilder()
        .WithHealth(InitialHealth)
        .Build();

    player.ReceiveDamage(FatalDamage);

    Assert.That(player.IsAlive, Is.False);
}
```

**Sin estándar**

```csharp
[Test]
public void Test_ReceiveFatalDamage_DamageExceedsHealth_UpdatesEverything()
{
    Player player = new PlayerBuilder()
        .WithHealth(InitialHealth)
        .Build();

    player.ReceiveDamage(FatalDamage);

    Assert.That(player.IsAlive, Is.False);
    Assert.That(player.Health, Is.EqualTo(MinimumHealth));
    Assert.That(player.CanAttack, Is.False);
}
```

**Excepciones esperadas**

Cuando se espere una excepción, `Assert.Throws<TException>()` será el único assert de la prueba (NUnit Project, s. f.-a; NUnit Project, s. f.-b).

**Con estándar**

```csharp
[Test]
public void Test_ReceiveDamage_DamageIsNegative_ThrowsArgumentOutOfRangeException()
{
    Player player = new PlayerBuilder().Build();

    TestDelegate receiveNegativeDamage = () =>
        player.ReceiveDamage(NegativeDamage);

    Assert.Throws<ArgumentOutOfRangeException>(
        receiveNegativeDamage);
}
```

**Sin estándar**

```csharp
[Test]
public void Test_ReceiveDamage_DamageIsNegative_ThrowsAndPreservesHealth()
{
    Player player = new PlayerBuilder().Build();

    Assert.Throws<ArgumentOutOfRangeException>(
        () => player.ReceiveDamage(NegativeDamage));
    Assert.That(player.Health, Is.EqualTo(DefaultHealth));
}
```

### 14.4 Mocking de dependencias

Los mocks deberán utilizarse únicamente para reemplazar dependencias externas o colaboradores cuyo comportamiento necesite controlarse durante una prueba (Microsoft, 2025b; NSubstitute, s. f.).

El código de producción deberá depender de interfaces recibidas mediante el constructor. No deberá crear internamente implementaciones concretas de sus dependencias (Martin, 2008; Microsoft, 2025b).

El proyecto utilizará exclusivamente NSubstitute como biblioteca de mocking. Las dependencias se configurarán mediante `Returns()` y las interacciones se verificarán mediante `Received()` (NSubstitute, s. f.).

**Dependencias mediante interfaces**

Las dependencias sustituibles deberán representarse mediante interfaces y recibirse mediante el constructor (Martin, 2008; Microsoft, 2025b).

**Con estándar**

```csharp
public interface IInventory
{
    void Add(Item item);
}

public sealed class RewardService
{
    private readonly IInventory _inventory;

    public RewardService(IInventory inventory)
    {
        _inventory = inventory;
    }

    public void GrantReward(Item reward)
    {
        _inventory.Add(reward);
    }
}
```

**Sin estándar**

```csharp
public sealed class RewardService
{
    private readonly Inventory _inventory = new Inventory();

    public void GrantReward(Item reward)
    {
        _inventory.Add(reward);
    }
}
```

**Biblioteca de mocking**

Todos los proyectos de pruebas deberán importar NSubstitute junto con NUnit. No se incluirán otras bibliotecas de mocking (NSubstitute, s. f.; NUnit Project, s. f.-c; convención interna del equipo).

**Con estándar**

```csharp
using NSubstitute;
using NUnit.Framework;
```

**Sin estándar**

```csharp
using NSubstitute;
using NUnit.Framework;
using OtherMockingLibrary;
```

**Configuración mediante NSubstitute**

Las dependencias deberán crearse mediante `Substitute.For<T>()`. Cuando sea necesario controlar el valor devuelto por un miembro, este se configurará mediante `Returns()` (NSubstitute, s. f.).

**Con estándar**

```csharp
[Test]
public void Test_LoadPlayer_SaveExists_ReturnsStoredPlayer()
{
    ISaveGameRepository saveGameRepository =
        Substitute.For<ISaveGameRepository>();
    Player expectedPlayer = new PlayerBuilder().Build();
    saveGameRepository.Load(PlayerSlot).Returns(expectedPlayer);
    LoadGameService loadGameService =
        new LoadGameService(saveGameRepository);

    Player actualPlayer = loadGameService.LoadPlayer(PlayerSlot);

    Assert.That(actualPlayer, Is.SameAs(expectedPlayer));
}
```

**Sin estándar**

```csharp
[Test]
public void Test_LoadPlayer_SaveExists_ReturnsStoredPlayer()
{
    FileSaveGameRepository saveGameRepository =
        new FileSaveGameRepository();
    LoadGameService loadGameService =
        new LoadGameService(saveGameRepository);

    Player actualPlayer = loadGameService.LoadPlayer(PlayerSlot);

    Assert.That(actualPlayer, Is.Not.Null);
}
```

**Verificación mediante NSubstitute**

Cuando se compruebe una interacción, `Received()` será la única verificación de la prueba. Se deberán especificar tanto la cantidad esperada de llamadas como los argumentos exactos (NSubstitute, s. f.; convención interna del equipo sobre cantidad y argumentos).

**Con estándar**

```csharp
[Test]
public void Test_GrantReward_RewardIsNotNull_AddsItemToInventory()
{
    IInventory inventory = Substitute.For<IInventory>();
    Item reward = new ItemBuilder().Build();
    RewardService rewardService = new RewardService(inventory);

    rewardService.GrantReward(reward);

    inventory.Received(1).Add(reward);
}
```

**Sin estándar**

```csharp
[Test]
public void Test_GrantReward_RewardIsNotNull_AddsItemToInventory()
{
    IInventory inventory = Substitute.For<IInventory>();
    Item reward = new ItemBuilder().Build();
    RewardService rewardService = new RewardService(inventory);

    rewardService.GrantReward(reward);

    inventory.Received().Add(Arg.Any<Item>());
    inventory.Received().Add(reward);
}
```

**Objetos que no deben sustituirse**

No se crearán mocks de entidades, objetos de valor ni de la clase que se está probando. Estos objetos deberán construirse directamente o mediante builders (Microsoft, 2025b; NSubstitute, s. f.).

**Con estándar**

```csharp
Player player = new PlayerBuilder()
    .WithHealth(InitialHealth)
    .Build();
```

**Sin estándar**

```csharp
Player player = Substitute.For<Player>();
player.Health.Returns(InitialHealth);
```

### 14.5 Métodos builder para objetos de prueba complejos

Los builders de prueba se utilizarán para crear objetos complejos con valores válidos por defecto. Su propósito será reducir la repetición y permitir que cada prueba sobrescriba únicamente los valores relevantes para el escenario evaluado (Fowler, 2018; Microsoft, 2025b).

Los builders se almacenarán dentro de `tests/AdventureGame.Tests.Unit/Builders`. Su nombre deberá terminar con el sufijo `Builder` (Fowler, 2018; convención interna del equipo para la ruta).

**Uso de builders para objetos complejos**

Se utilizará un builder cuando la creación directa de un objeto necesite varios parámetros o configuraciones (Fowler, 2018; Microsoft, 2025b).

**Con estándar**

```csharp
Player player = new PlayerBuilder()
    .WithHealth(LowHealth)
    .WithLevel(InitialLevel)
    .Build();
```

**Sin estándar**

```csharp
Player player = new Player(
    PlayerId,
    "Player",
    LowHealth,
    MaximumHealth,
    InitialLevel,
    InitialExperience,
    InitialGold,
    new List<Item>(),
    defaultWeapon,
    defaultArmor);
```

**Nomenclatura de builders**

La clase deberá utilizar el nombre del objeto construido y el sufijo `Builder`. Los métodos de configuración deberán utilizar el prefijo `With` y escribirse en `PascalCase` (Fowler, 2018; Microsoft, 2026b; convención interna del equipo).

**Con estándar**

```csharp
public sealed class PlayerBuilder
{
    public PlayerBuilder WithHealth(int health)
    {
        _health = health;
        return this;
    }
}
```

**Sin estándar**

```csharp
public sealed class PlayerMaker
{
    public PlayerMaker SetHp(int hp)
    {
        _health = hp;
        return this;
    }
}
```

**Valores válidos por defecto**

Un builder deberá producir un objeto válido aunque no se invoque ningún método `With`. Los valores predeterminados deberán representar el caso más común y neutral (Fowler, 2018; Microsoft, 2025b).

**Con estándar**

```csharp
public sealed class PlayerBuilder
{
    private const int DefaultHealth = 100;
    private const int DefaultLevel = 1;
    private const string DefaultName = "Player";

    private int _health = DefaultHealth;
    private int _level = DefaultLevel;
    private string _name = DefaultName;

    public Player Build()
    {
        Player player = new Player(
            _name,
            _health,
            _level);

        return player;
    }
}
```

**Sin estándar**

```csharp
public sealed class PlayerBuilder
{
    private int _health;
    private int _level;
    private string? _name;

    public Player Build()
    {
        Player player = new Player(
            _name,
            _health,
            _level);

        return player;
    }
}
```

**Modificación de una propiedad por método**

Cada método `With` deberá modificar una sola característica del objeto. No se utilizará un método para configurar varias propiedades sin relación directa (Fowler, 2018; Martin, 2008).

**Con estándar**

```csharp
public PlayerBuilder WithHealth(int health)
{
    _health = health;
    return this;
}
```

**Sin estándar**

```csharp
public PlayerBuilder WithCombatValues(
    int health,
    int level,
    int attackPower)
{
    _health = health;
    _level = level;
    _attackPower = attackPower;
    return this;
}
```

**Retorno del propio builder**

Los métodos `With` deberán devolver la instancia actual mediante `return this;` para permitir el encadenamiento de llamadas (Fowler, 2018).

**Con estándar**

```csharp
public PlayerBuilder WithLevel(int level)
{
    _level = level;
    return this;
}
```

**Sin estándar**

```csharp
public void WithLevel(int level)
{
    _level = level;
}

```

**Creación de una instancia nueva**

El método `Build()` deberá devolver una nueva instancia en cada llamada. No deberá reutilizar un objeto mutable construido anteriormente (Fowler, 2018; Microsoft, 2025b).

**Con estándar**

```csharp
public Player Build()
{
    List<Item> inventoryCopy = new List<Item>(_items);
    Player player = new Player(
        _name,
        _health,
        _level,
        inventoryCopy);

    return player;
}
```

**Sin estándar**

```csharp
private readonly Player _player = new Player();

public Player Build()
{
    _player.Name = _name;
    _player.Health = _health;
    _player.Level = _level;

    return _player;
}
```

**Ausencia de validaciones y asserts**

Los builders no deberán contener asserts ni reglas de prueba. Su única responsabilidad será construir objetos (Fowler, 2018; Microsoft, 2025b).

**Con estándar**

```csharp
public Player Build()
{
    Player player = new Player(
        _name,
        _health,
        _level);

    return player;
}
```

**Sin estándar**

```csharp
public Player Build()
{
    Assert.That(_health, Is.GreaterThan(MinimumHealth));

    Player player = new Player(
        _name,
        _health,
        _level);

    return player;
}
```

**Configuración mínima dentro de la prueba**

Cada prueba deberá modificar únicamente las propiedades necesarias para representar su escenario (Microsoft, 2025b; Fowler, 2018).

**Con estándar**

```csharp
[Test]
public void Test_IsAlive_HealthIsZero_ReturnsFalse()
{
    Player player = new PlayerBuilder()
        .WithHealth(MinimumHealth)
        .Build();

    bool isAlive = player.IsAlive;

    Assert.That(isAlive, Is.False);
}
```

**Sin estándar**

```csharp
[Test]
public void Test_IsAlive_HealthIsZero_ReturnsFalse()
{
    Player player = new PlayerBuilder()
        .WithName("Player")
        .WithHealth(MinimumHealth)
        .WithLevel(InitialLevel)
        .WithExperience(InitialExperience)
        .WithGold(InitialGold)
        .WithWeapon(defaultWeapon)
        .WithArmor(defaultArmor)
        .Build();

    bool isAlive = player.IsAlive;

    Assert.That(isAlive, Is.False);
}
```

## 15. Dependencias externas

### 15.1 Librerías/paquetes utilizados

| Paquete | Uso en el proyecto |
| --- | --- |
| `log4net` | Registro de eventos mediante los niveles `Debug`, `Info`, `Warn`, `Error` y `Fatal`. |
| `log4net.Ext.Trace` | Incorporación del nivel `Trace` requerido por este estándar. |
| `NUnit` | Escritura y ejecución de pruebas unitarias y de integración. |
| `NSubstitute` | Sustitución de dependencias en pruebas. |

Los usos asignados a estas dependencias corresponden con la documentación de sus respectivos proyectos (Apache Logging Services, s. f.-a, s. f.-b; NSubstitute, s. f.; NUnit Project, s. f.-c).

### 15.2 Vulnerabilidades conocidas (formato CVE, aplica/no aplica)


## 16 Comunicación en red y operaciones asíncronas

El proyecto utiliza una arquitectura cliente-servidor (ver STK-07, Programador de red), por lo que toda operación que dependa de la red — enviar una jugada, sincronizar el estado de la partida, autenticar a un jugador — se ejecutará de forma asíncrona y no deberá bloquear el hilo principal del juego. Esta sección define cómo se estructuran esas llamadas, cómo se exponen sus resultados mediante callbacks o async/await, y cómo se integran con el manejo de errores ya definido en la sección 7 (Microsoft, s. f.-a; Microsoft, s. f.-b)

### 16.1 Patrón de llamadas asíncronas (async/await)

Toda operación de red se expondrá mediante métodos async que devuelvan Task o Task<TResult>. No se utilizará async void, salvo en manejadores de eventos de UI, donde es la única forma admitida por la firma del delegado. El sufijo Async se agregará al nombre del método, de acuerdo con las convenciones oficiales para el patrón basado en tareas (Microsoft, s. f.-a; Microsoft, s. f.-c)

**Con estándar**

```csharp

public sealed class MatchmakingService
{
    private readonly IMatchmakingClient _matchmakingClient;

    public MatchmakingService(IMatchmakingClient matchmakingClient)
    {
        _matchmakingClient = matchmakingClient;
    }

    public async Task<MatchResult> JoinMatchAsync(string playerId)
    {
        MatchResult matchResult = await _matchmakingClient.RequestMatchAsync(playerId);

        return matchResult;
    }
}
```

**Sin estándar**

```csharp

public sealed class MatchmakingService
{
    public async void JoinMatch(string playerId)
    {
        MatchResult matchResult = await matchmakingClient.RequestMatch(playerId);
    }
}
````

### 16.2 Callbacks y manejadores de eventos de red

Cuando una operación de red deba notificar un resultado fuera del flujo async/await (por ejemplo, un mensaje entrante del servidor que no fue solicitado directamente por el cliente), se expondrá mediante un evento siguiendo las reglas ya definidas en la sección 4.9, no mediante un delegado Action<T> suelto ni un callback pasado como parámetro.

**Con estándar**

```csharp

public sealed class GameConnection
{
    public event EventHandler<OpponentMoveReceivedEventArgs>? OpponentMoveReceived;

    protected virtual void OnOpponentMoveReceived(OpponentMoveReceivedEventArgs e)
    {
        OpponentMoveReceived?.Invoke(this, e);
    }
}
````

**Sin estándar**

```csharp

public sealed class GameConnection
{
    public Action<Move>? OnMoveReceived;
}
````

### 16.3 Manejo de errores en operaciones de red

Las excepciones producidas por fallas de red (tiempo de espera agotado, conexión perdida, respuesta inválida del servidor) se manejarán siguiendo las reglas generales de la sección 7. Los servicios de red podrán lanzar TimeoutException u OperationCanceledException conforme a la tabla de la sección 7.1, o envolver el fallo en una excepción de dominio propia (por ejemplo, ConnectionLostException) cuando el consumidor necesite distinguir ese caso de un error genérico.

**Con estándar**

```csharp

public async Task<MatchResult> JoinMatchAsync(string playerId)
{
    try
    {
        MatchResult matchResult = await _matchmakingClient.RequestMatchAsync(playerId);

        return matchResult;
    }
    catch (TaskCanceledException exception)
    {
        throw new ConnectionLostException(
            "The matchmaking request timed out.",
            exception);
    }
}
````

**Sin estándar**

```csharp

public async Task<MatchResult> JoinMatchAsync(string playerId)
{
    try
    {
        return await _matchmakingClient.RequestMatchAsync(playerId);
    }
    catch
    {
        return null;
    }
}
````

### 16.4 Cancelación de operaciones asíncronas

Toda operación de red de larga duración deberá aceptar un parámetro CancellationToken como último parámetro del método, para permitir que el llamador cancele la operación cuando el jugador abandone la partida o cierre la aplicación (Microsoft, s. f.-a).

**Con estándar**

```csharp

public async Task<MatchResult> JoinMatchAsync(
    string playerId,
    CancellationToken cancellationToken)
{
    MatchResult matchResult = await _matchmakingClient.RequestMatchAsync(
        playerId,
        cancellationToken);

    return matchResult;
}
````

**Sin estándar**

```csharp

public async Task<MatchResult> JoinMatchAsync(string playerId)
{
    MatchResult matchResult = await _matchmakingClient.RequestMatchAsync(playerId);

    return matchResult;
}
````


## 17. Declaración de uso de inteligencia artificial


<div style="page-break-after: always;"></div>

## 18. Referencias

- Apache Logging Services. (s. f.-a). *Apache log4net release notes*. Recuperado el 25 de agosto de 2026, de [https://logging.apache.org/log4net/log4net-3.0.0/release/release-notes.html](https://logging.apache.org/log4net/log4net-3.0.0/release/release-notes.html)

- Apache Logging Services. (s. f.-b). *Introduction*. Recuperado el 25 de agosto de 2026, de [https://logging.apache.org/log4net/manual/introduction.html](https://logging.apache.org/log4net/manual/introduction.html)

- Cwalina, K., Barton, J., & Abrams, B. (2020). *Framework design guidelines: Conventions, idioms, and patterns for reusable .NET libraries* (3.ª ed.). Addison-Wesley Professional. [https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780135896372](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780135896372)

- Microsoft. (2023a, 3 de octubre). *Names of type members*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members)

- Microsoft. (2023b, 3 de noviembre). *Creating and throwing exceptions*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/creating-and-throwing-exceptions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/creating-and-throwing-exceptions)

- Microsoft. (2023c, 17 de mayo). *SYSLIB0051: Legacy serialization support APIs are obsolete*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/fundamentals/syslib-diagnostics/syslib0051](https://learn.microsoft.com/en-us/dotnet/fundamentals/syslib-diagnostics/syslib0051)

- Microsoft. (2024a, 27 de septiembre). *C# compiler options for language feature rules*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/compiler-options/language](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/compiler-options/language)

- Microsoft. (2024b, 30 de octubre). *Restricting accessor accessibility*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility)

- Microsoft. (2025a, 22 de octubre). *Best practices for exceptions*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions](https://learn.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions)

- Microsoft. (2025b, 22 de marzo). *Best practices for writing unit tests*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices)

- Microsoft. (2025c, 30 de enero). *C# formatting options*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options)

- Microsoft. (2025d, 18 de enero). *Common C# code conventions*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)

- Microsoft. (2025e, 29 de mayo). *Names of classes, structs, and interfaces*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces)

- Microsoft. (2025f, 19 de noviembre). *Properties*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties)

- Microsoft. (2026a, 2 de abril). *CA1031: Do not catch general exception types*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/quality-rules/ca1031](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/quality-rules/ca1031)

- Microsoft. (2026b, 14 de julio). *C# identifier naming rules and conventions*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names)

- Microsoft. (2026c, 20 de enero). *Selection statements: `if`, `if-else`, and `switch`*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements)

- Microsoft. (2026d, 24 de marzo). *`switch` expression: Pattern matching expressions using the `switch` keyword*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression)

- Microsoft. (2026e, 14 de agosto). *Recommended XML documentation tags*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/recommended-tags](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/recommended-tags)

- NSubstitute. (s. f.). *Getting started*. Recuperado el 22 de agosto de 2026, de [https://nsubstitute.github.io/help/getting-started/](https://nsubstitute.github.io/help/getting-started/)

- NUnit Project. (s. f.-a). *Assert.Throws*. Recuperado el 22 de agosto de 2026, de [https://docs.nunit.org/articles/nunit/writing-tests/assertions/classic-assertions/Assert.Throws.html](https://docs.nunit.org/articles/nunit/writing-tests/assertions/classic-assertions/Assert.Throws.html)

- NUnit Project. (s. f.-b). *Assertions*. Recuperado el 22 de agosto de 2026, de [https://docs.nunit.org/articles/nunit/writing-tests/assertions/assertions.html](https://docs.nunit.org/articles/nunit/writing-tests/assertions/assertions.html)

- NUnit Project. (s. f.-c). *Test*. Recuperado el 22 de agosto de 2026, de [https://docs.nunit.org/articles/nunit/writing-tests/attributes/test.html](https://docs.nunit.org/articles/nunit/writing-tests/attributes/test.html)

- NUnit Project. (s. f.-d). *TestCase*. Recuperado el 22 de agosto de 2026, de [https://docs.nunit.org/articles/nunit/writing-tests/attributes/testcase.html](https://docs.nunit.org/articles/nunit/writing-tests/attributes/testcase.html)

- NUnit Project. (s. f.-e). *TestFixture*. Recuperado el 22 de agosto de 2026, de [https://docs.nunit.org/articles/nunit/writing-tests/attributes/testfixture.html](https://docs.nunit.org/articles/nunit/writing-tests/attributes/testfixture.html)

- Fowler, M. (2018). Refactoring: Improving the design of existing code (2nd ed.). Addison-Wesley.
  
- Martin, R. C. (2008). Clean code: A handbook of agile software craftsmanship. Prentice Hall.

- McCabe, T. J. (1976). A complexity measure. IEEE Transactions on Software Engineering, SE-2(4), 308–320. https://doi.org/10.1109/TSE.1976.233837

- McConnell, S. (2004). Code complete (2nd ed.). Microsoft Press.

- Chuvakin, A., Schmidt, K., & Phillips, C. (2013). Logging and log management: The authoritative guide to understanding the concepts surrounding logging and log management. Syngress.

- Microsoft. (s. f.-a). Asynchronous programming with async and await. Microsoft Learn. Recuperado el 29 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/

- Microsoft. (s. f.-b). Task asynchronous programming model. Microsoft Learn. Recuperado el 29 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/task-asynchronous-programming-model

- Microsoft. (s. f.-c). Task-based Asynchronous Pattern (TAP). Microsoft Learn. Recuperado el 29 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap

- Microsoft. (s. f.-d). Event-based Asynchronous Pattern (EAP) overview. Microsoft Learn. Recuperado el 29 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap-overview
  
- Microsoft. (s. f.-e). Static constructors. Microsoft Learn. Recuperado el 29 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/static-constructors

- Microsoft. (s. f.-f). Records. Microsoft Learn. Recuperado el 29 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/records

- Microsoft. (s. f.-g). Auto-implemented properties. Microsoft Learn. Recuperado el 29 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties

- Microsoft. (s. f.-h). Resources in .NET apps. Microsoft Learn. Recuperado el 29 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/core/extensions/resources-and-localization
