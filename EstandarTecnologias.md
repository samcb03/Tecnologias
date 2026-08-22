# Estándar de codificación

## 1. Introducción
### 1.1 Problemática
### 1.2 Propósito
### 1.3 Idioma del código

## 2. Organización del proyecto
### 2.1 Stack tecnológico y entorno de desarrollo
### 2.2 Arquitectura general (patrones: MVC/MVP, Observer, Singleton para managers, ECS si aplica)
### 2.3 Estructura de carpetas y namespaces
### 2.4 Separación MonoBehaviour / clases puras (POCO) / ScriptableObjects

## 3. Control de versiones
### 3.1 Commits
### 3.2 .gitignore y Git LFS (assets binarios)

## 4. Formato general de cada regla (aplica a las secciones 5–15)

## 5 Reglas de nombrado

Los identificadores deberán escribirse en inglés y describir claramente su propósito. Se priorizará la claridad sobre la brevedad y se evitarán abreviaturas, palabras reservadas y nombres de un solo carácter, excepto en contadores de ciclos de alcance menor a 3 lineas.

No se utilizarán dos guiones bajos consecutivos, ya que estos nombres están reservados para identificadores generados por el compilador.

C# utiliza principalmente:

- `PascalCase` para clases, estructuras, interfaces, métodos, propiedades, eventos, constantes y espacios de nombres.
- `camelCase` para variables locales y parámetros.
- `_camelCase` para campos de instancia privados o internos.
- `s_camelCase` para campos estáticos privados o internos.

Estas reglas corresponden a las [convenciones oficiales para identificadores de C#](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names).
### 5.1 Variables y parámetros

Las variables locales y los parámetros deberán escribirse utilizando `camelCase`. Sus nombres deberán ser sustantivos o frases nominales que permitan comprender qué información almacenan.

Se evitarán nombres de un solo carácter, excepto en contadores de ciclos simples como `i`, `j` o `k` o en excepciones como `e`.

**Con estándar**

```csharp
int remainingLives = 3;
```

**Sin estándar**

```csharp
int rl = 3;
```

Los parámetros también deberán tener nombres descriptivos.

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
### 5.2 Colecciones

Las variables y propiedades que representen colecciones deberán utilizar nombres en plural para indicar que contienen varios elementos.

**Con estándar**

```csharp
List<Enemy> activeEnemies = new();
```

**Sin estándar**

```csharp
List<Enemy> activeEnemy = new();
```

El nombre no deberá incluir palabras como `List` o `Collection` cuando el plural ya permita identificar claramente su contenido.
### 5.3 Booleanos

Los identificadores booleanos deberán expresar una condición afirmativa. Cuando ayude a comprender su significado, se utilizarán prefijos como `Is`, `Has` o `Can`, respetando el tipo de capitalización correspondiente.

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
### 5.4 Declaración y sombreado de variables

Se deberá declarar una sola variable por línea para mejorar la claridad del código.

**Con estándar**

```csharp
int playerScore = 0;
int enemyScore = 0;
```

**Sin estándar**

```csharp
int playerScore = 0, enemyScore = 0;
```

También deberá evitarse el sombreado, que ocurre cuando una variable local utiliza el mismo nombre que un campo de la clase.

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
### 5.5 Campos privados e internos

Los campos de instancia privados o internos deberán escribirse utilizando `_camelCase`.

**Con estándar**

```csharp
private int _currentHealth;
private string _playerName;
```

**Sin estándar**

```csharp
private int currentHealth;
private string PlayerName;
```

Los campos estáticos privados o internos deberán escribirse utilizando el prefijo `s_` seguido de `camelCase`.

**Con estándar**

```csharp
private static int s_activeEnemyCount;
```

**Sin estándar**

```csharp
private static int activeEnemyCount;
```
### 5.6 Propiedades

Los nombres de las propiedades deberán escribirse en `PascalCase` y utilizar sustantivos, frases nominales o adjetivos que describan el dato representado.

**Con estándar**

```csharp
public int CurrentHealth { get; private set; }
public string CharacterName { get; private set; }
public bool IsInvulnerable { get; private set; }
```

**Sin estándar**

```csharp
public int currentHealth { get; private set; }
public string character_name { get; private set; }
public bool InvulnerabilityFlag { get; private set; }
```

Las propiedades booleanas deberán expresar condiciones afirmativas y las propiedades de colecciones deberán utilizar nombres en plural. Estas recomendaciones aparecen en las [convenciones oficiales para miembros de tipos](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members).
### 5.7 Constantes

Las constantes de C# deberán escribirse en `PascalCase`. Esta regla se aplicará tanto a constantes públicas como privadas y locales.

**Con estándar**

```csharp
private const int MaximumLives = 3;
```

**Sin estándar**

```csharp
private const int MAXIMUM_LIVES = 3;
```

Las constantes deberán representar valores que no cambien durante la ejecución.
### 5.8 Métodos

Los métodos y las funciones locales deberán escribirse utilizando `PascalCase`. Sus nombres deberán ser verbos o frases verbales que indiquen claramente la acción que realizan.

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
### 5.9 Eventos

Los eventos deberán escribirse utilizando `PascalCase` y nombrarse con verbos o frases verbales. Se utilizará el presente para eventos que ocurren antes de una acción y el pasado para los que ocurren después.

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

Los métodos protegidos que disparen un evento deberán comenzar con `On`, seguido del nombre del evento. Los parámetros de un manejador de eventos deberán llamarse `sender` y `e`, de acuerdo con las [convenciones oficiales de eventos de .NET](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/event).
### 5.10 Métodos de prueba unitaria

Los métodos de prueba deberán utilizar el siguiente formato:

```text
Test_NombreMetodo_Flujo_Resultado
```

Cada parte tendrá la siguiente función:

- Test: prefijo obligatorio que identifica el método como una prueba.
- NombreMetodo: nombre exacto del método que se está probando.
- Flujo: condición o flujo de ejecución evaluado.
- Resultado: comportamiento esperado.

Las partes deberán escribirse en PascalCase y separarse mediante guiones bajos.

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

Este formato coincide con las [prácticas oficiales de Microsoft para nombrar pruebas unitarias](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices).
### 5.11 Clases, estructuras y registros

Los nombres de clases, estructuras y registros deberán escribirse utilizando `PascalCase`. Deberán ser sustantivos o frases nominales que describan la entidad o concepto que representan.

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
### 5.12 Interfaces

Las interfaces deberán escribirse utilizando `PascalCase` y comenzar con la letra mayúscula `I`.

**Con estándar**

```csharp
public interface IEnemySpawner 
{ 
}
```

**Sin estándar**

```csharp
public interface EnemySpawnerInterface 
{ 
}
```

Cuando una clase sea la implementación principal de una interfaz, sus nombres deberán diferenciarse únicamente por el prefijo `I`.

**Con estándar**

```csharp
public interface IEnemySpawner 
{ 
}

public class EnemySpawner : IEnemySpawner 
{ 
}
```

**Sin estándar**

```csharp
public interface SpawnerInterface 
{ 
}

public class DefaultEnemyGenerator : SpawnerInterface 
{ 
}
```

Las reglas para clases e interfaces están recogidas en las [guías oficiales de diseño de .NET](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces).
### 5.13 Parámetros de tipo genérico

Los parámetros genéricos deberán comenzar con la letra mayúscula `T`. Se podrá utilizar únicamente `T` cuando el significado sea evidente o un nombre descriptivo como `TEntity` cuando proporcione mayor claridad.

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
### 5.14 Enumeraciones

Los nombres de las enumeraciones y sus valores deberán escribirse utilizando `PascalCase`.

Las enumeraciones normales deberán utilizar un nombre singular. Las enumeraciones que representen una combinación de indicadores deberán utilizar un nombre plural. No se agregarán los sufijos `Enum`, `Flag` o `Flags`.

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
### 5.15 Espacios de nombres

Los espacios de nombres deberán utilizar `PascalCase`. Sus componentes se separarán mediante puntos y deberán representar de forma clara el proyecto y la funcionalidad agrupada.

**Con estándar**

```csharp
namespace CompanyName.GameName.Combat;
```

**Sin estándar**

```csharp
namespace company_name.game_name.combat;
```
### 5.16 Sufijos oficiales por responsabilidad

Se utilizarán los siguientes sufijos cuando el tipo cumpla realmente con la responsabilidad correspondiente:

- `Exception`: excepciones personalizadas.
- `EventArgs`: clases que contienen información de un evento.
- `EventHandler`: delegados personalizados utilizados para eventos.
- `Attribute`: atributos personalizados.
- `Collection`: tipos especializados de colección.
- `Dictionary`: tipos especializados de diccionario.
- `Stream`: tipos especializados de flujo de datos.

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

## 6 Estilo de código

El código deberá mantener un formato uniforme que facilite su lectura, revisión y mantenimiento. Las reglas de esta sección se aplicarán a todos los archivos C# del videojuego.

Se utilizarán cuatro espacios para la indentación, llaves con estilo Allman, una instrucción por línea y líneas de continuación indentadas. Estas reglas toman como base las [convenciones de código oficiales de C#](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions).

Las reglas relacionadas con números mágicos, complejidad ciclomática, cantidad de parámetros y operadores lógicos se establecerán en la sección 9 del estándar.

### 6.1 Formato general (indentación, límite de columnas)

**Indentación de cuatro espacios**

Por cada nivel de indentación se utilizarán cuatro espacios.

**Con estándar**

```csharp
if (player.IsAlive)
{
    player.Attack();
}
```

**Sin estándar**

```csharp
if (player.IsAlive)
{
  player.Attack();
}
```

**Uso de espacios en lugar de tabuladores**

La indentación deberá realizarse con espacios. No se utilizarán tabuladores, ya que su anchura puede cambiar entre editores.

**Con estándar**

```csharp
while (enemy.IsAlive)
{
    enemy.UpdateBehavior();
}
```

**Sin estándar**

```csharp
while (enemy.IsAlive)
{
	enemy.UpdateBehavior();
}
```

**Colocación de llaves**

Las llaves deberán seguir el estilo Allman. La llave de apertura y la llave de cierre se colocarán en líneas independientes y alineadas con la declaración correspondiente.

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

Cada línea deberá contener una sola instrucción.

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

Cada variable deberá declararse en una línea independiente.

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

Ninguna línea deberá superar los 120 caracteres. Cuando una instrucción exceda el límite, deberá dividirse en varias líneas.

**Con estándar**

```csharp
BattleResult battleResult = battleService.ResolveBattle(
    player,
    enemy,
    selectedDifficulty,
    currentLevel,
    battleRules);
```

**Sin estándar**

```csharp
BattleResult battleResult = battleService.ResolveBattle(player, enemy, selectedDifficulty, currentLevel, battleRules, availableRewards);
```

**Indentación de líneas de continuación**

Las líneas de continuación deberán indentarse cuatro espacios adicionales respecto de la línea original. Cuando una expresión se divida antes de un operador, todos los operadores deberán mantener la misma alineación.

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

Cuando una llamada deba dividirse por superar el límite de columna, se colocará un argumento por línea. El paréntesis de cierre se alineará con el inicio de la instrucción.

**Con estándar**

```csharp
Enemy enemy = enemyFactory.Create(
    enemyType,
    spawnPosition,
    initialHealth,
    attackPower);
```

**Sin estándar**

```csharp
Enemy enemy = enemyFactory.Create(enemyType,
    spawnPosition, initialHealth,
        attackPower);
```

### 6.2 Espacios en blanco (vertical/horizontal)

**Separación entre secciones del archivo**

Se dejará una línea en blanco entre el bloque de directivas `using`, la declaración del espacio de nombres y la declaración del tipo.

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

Se dejará una línea en blanco entre campos, constructores, propiedades y métodos cuando pertenezcan a grupos distintos.

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

Se dejará una línea en blanco entre dos métodos consecutivos.

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

Dentro de un método se utilizará una línea en blanco cuando sea necesario distinguir dos etapas lógicas de una operación.

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

No se utilizarán varias líneas en blanco consecutivas. Una sola línea será suficiente para separar bloques relacionados.

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

Se colocará un espacio después de las palabras clave `if`, `for`, `foreach`, `while`, `switch`, `catch` y `using` cuando estén seguidas de una expresión.

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

Se colocará un espacio a cada lado de los operadores binarios, como `=`, `+`, `-`, `==`, `!=`, `&&` y `||`.

**Con estándar**

```csharp
int totalDamage = baseDamage + bonusDamage;
```

**Sin estándar**

```csharp
int totalDamage=baseDamage+bonusDamage;
```

**Espacio entre un método y su paréntesis**

No se colocará un espacio entre el nombre de un método y el paréntesis de apertura.

**Con estándar**

```csharp
player.RestoreHealth();
```

**Sin estándar**

```csharp
player.RestoreHealth ();
```

**Espacios dentro de paréntesis**

No se colocarán espacios inmediatamente después de un paréntesis de apertura ni antes de uno de cierre.

**Con estándar**

```csharp
enemy.ReceiveDamage(damage);
```

**Sin estándar**

```csharp
enemy.ReceiveDamage( damage );
```

**Espacio después de comas**

Se colocará un espacio después de cada coma que separe argumentos, parámetros o elementos.

**Con estándar**

```csharp
MovePlayer(horizontalDirection, verticalDirection);
```

**Sin estándar**

```csharp
MovePlayer(horizontalDirection,verticalDirection);
```

**Espaciado de operadores unarios**

Los operadores unarios, como `!`, `++` y `--`, no se separarán de su operando.

**Con estándar**

```csharp
remainingEnemies--;
```

**Sin estándar**

```csharp
remainingEnemies --;
```

**Alineación manual con espacios**

No se agregarán espacios adicionales para alinear declaraciones manualmente. Cada elemento deberá conservar únicamente el espacio requerido por la sintaxis.

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

### 6.3 Organización del archivo (orden de `using`)

**Ubicación de las directivas `using`**

Las directivas `using` deberán colocarse fuera de la declaración del espacio de nombres.

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

**Orden de los grupos de directivas `using`**

Primero se colocarán los espacios de nombres del sistema, después los de bibliotecas externas y finalmente los pertenecientes al proyecto.

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

Las directivas `using` deberán ordenarse alfabéticamente dentro del grupo al que pertenezcan.

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

**Separación entre grupos de directivas `using`**

Los grupos de directivas `using` deberán separarse mediante una línea en blanco.

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

No se conservarán directivas `using` duplicadas ni directivas que no sean utilizadas por el archivo.

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

Los alias y las directivas `using static` se colocarán después de las directivas ordinarias. Solo se utilizarán cuando eviten una ambigüedad o mejoren claramente la lectura.

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

Se utilizará una declaración de espacio de nombres con ámbito de archivo para evitar un nivel de indentación innecesario.

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

Cada archivo deberá contener un único tipo público principal. El nombre del archivo deberá coincidir con el nombre de ese tipo.

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

### 6.4 Orden de miembros de la clase

Los miembros de una clase deberán conservar el siguiente orden general:

1. Constantes.
2. Campos estáticos.
3. Campos de instancia.
4. Constructores.
5. Eventos.
6. Propiedades.
7. Métodos de ciclo de vida.
8. Métodos públicos.
9. Métodos protegidos.
10. Métodos privados.
11. Tipos anidados.

**Posición de las constantes**

Las constantes deberán colocarse antes de los campos estáticos y de instancia.

**Con estándar**

```csharp
private const int DefaultHealth = 100;
private static int s_activePlayers;
private int _currentHealth;
```

**Sin estándar**

```csharp
private static int s_activePlayers;
private int _currentHealth;
private const int DefaultHealth = 100;
```

**Posición de los campos estáticos**

Los campos estáticos deberán colocarse después de las constantes y antes de los campos de instancia.

**Con estándar**

```csharp
private static int s_activeEnemies;
private readonly EnemyFactory _enemyFactory;
```

**Sin estándar**

```csharp
private readonly EnemyFactory _enemyFactory;
private static int s_activeEnemies;
```

**Posición de los campos de instancia**

Los campos de instancia deberán colocarse antes de los constructores.

**Con estándar**

```csharp
private readonly Player _player;

public PlayerController(Player player)
{
    _player = player;
}
```

**Sin estándar**

```csharp
public PlayerController(Player player)
{
    _player = player;
}

private readonly Player _player;
```

**Posición de los constructores**

Los constructores deberán colocarse después de los campos y antes de los eventos y propiedades.

**Con estándar**

```csharp
private readonly Player _player;

public PlayerController(Player player)
{
    _player = player;
}

public event Action? PlayerDefeated;
```

**Sin estándar**

```csharp
public event Action? PlayerDefeated;

public PlayerController(Player player)
{
    _player = player;
}

private readonly Player _player;
```

**Posición de los eventos**

Los eventos deberán colocarse después de los constructores y antes de las propiedades.

**Con estándar**

```csharp
public event Action? PlayerDefeated;

public int CurrentHealth { get; private set; }
```

**Sin estándar**

```csharp
public int CurrentHealth { get; private set; }

public event Action? PlayerDefeated;
```

**Posición de las propiedades**

Las propiedades deberán colocarse después de los eventos y antes de los métodos de ciclo de vida.

**Con estándar**

```csharp
public int CurrentHealth { get; private set; }

private void Awake()
{
    InitializePlayer();
}
```

**Sin estándar**

```csharp
private void Awake()
{
    InitializePlayer();
}

public int CurrentHealth { get; private set; }
```

**Posición de los métodos de ciclo de vida**

Los métodos de ciclo de vida deberán colocarse después de las propiedades y antes de los demás métodos, aunque su nivel de acceso sea privado.

**Con estándar**

```csharp
public int CurrentHealth { get; private set; }

private void Update()
{
    ProcessPlayerInput();
}

public void ReceiveDamage(int damage)
{
    CurrentHealth -= damage;
}
```

**Sin estándar**

```csharp
public void ReceiveDamage(int damage)
{
    CurrentHealth -= damage;
}

private void Update()
{
    ProcessPlayerInput();
}

public int CurrentHealth { get; private set; }
```

**Orden de los métodos de ciclo de vida**

Cuando existan, los métodos de ciclo de vida deberán mantener el siguiente orden: `Awake`, `OnEnable`, `Start`, `Update`, `FixedUpdate`, `LateUpdate`, `OnDisable` y `OnDestroy`.

**Con estándar**

```csharp
private void Awake()
{
    InitializePlayer();
}

private void OnEnable()
{
    SubscribeToEvents();
}

private void Start()
{
    SpawnPlayer();
}

private void Update()
{
    ProcessPlayerInput();
}

private void FixedUpdate()
{
    ApplyPlayerMovement();
}

private void LateUpdate()
{
    UpdateViewTarget();
}

private void OnDisable()
{
    UnsubscribeFromEvents();
}

private void OnDestroy()
{
    ReleasePlayerResources();
}
```

**Sin estándar**

```csharp
private void Update()
{
    ProcessPlayerInput();
}

private void Awake()
{
    InitializePlayer();
}

private void OnDestroy()
{
    ReleasePlayerResources();
}

private void Start()
{
    SpawnPlayer();
}

private void OnEnable()
{
    SubscribeToEvents();
}

private void LateUpdate()
{
    UpdateViewTarget();
}

private void FixedUpdate()
{
    ApplyPlayerMovement();
}

private void OnDisable()
{
    UnsubscribeFromEvents();
}
```

**Declaración de métodos de ciclo de vida necesarios**

No se declararán métodos de ciclo de vida vacíos únicamente para completar la lista. Solo deberán incluirse los que realicen una operación necesaria.

**Con estándar**

```csharp
private void Awake()
{
    InitializePlayer();
}

private void Update()
{
    ProcessPlayerInput();
}
```

**Sin estándar**

```csharp
private void Awake()
{
    InitializePlayer();
}

private void OnEnable()
{
}

private void Start()
{
}

private void Update()
{
    ProcessPlayerInput();
}
```

**Orden de métodos según su visibilidad**

Después de los métodos de ciclo de vida se colocarán primero los métodos públicos, después los protegidos y finalmente los privados.

**Con estándar**

```csharp
public void Attack()
{
    ExecuteAttack();
}

protected void PrepareAttack()
{
    weapon.Prepare();
}

private void ExecuteAttack()
{
    weapon.Use();
}
```

**Sin estándar**

```csharp
private void ExecuteAttack()
{
    weapon.Use();
}

public void Attack()
{
    ExecuteAttack();
}

protected void PrepareAttack()
{
    weapon.Prepare();
}
```

**Posición de los tipos anidados**

Las clases, estructuras, enumeraciones o interfaces anidadas deberán colocarse después de todos los demás miembros de la clase.

**Con estándar**

```csharp
private void ChangeState(EnemyState state)
{
    _currentState = state;
}

private enum EnemyState
{
    Idle,
    Chasing,
    Attacking
}
```

**Sin estándar**

```csharp
private enum EnemyState
{
    Idle,
    Chasing,
    Attacking
}

private void ChangeState(EnemyState state)
{
    _currentState = state;
}
```

## 7. Estructuras de control
### 7.1 Llaves

El uso de llaves será obligatorio en la totalidad de las estructuras de control (if, else, for, while, do-while, switch), sin excepción para bloques que contengan una única instrucción. Siguiendo el estilo de indentación definido, la llave de apertura deberá posicionarse en una línea independiente, alineada con el inicio de la instrucción precedente; de igual manera, la llave de cierre ocupará su propia línea en el mismo nivel jerárquico.

Bajo las directrices oficiales de desarrollo para C#, se adopta el estilo Allman, el cual ubica la llave de apertura en una nueva línea para bloques lógicos, métodos y definiciones de tipos ([Microsoft, 2024](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)). Se mantiene la restricción de omitir llaves en cuerpos simples como una medida preventiva de seguridad técnica; esta práctica mitiga el riesgo de introducir errores lógicos al añadir instrucciones adicionales de manera accidental, garantizando que la estructura sintáctica sea explícita y no dependa únicamente de la indentación visual del código.

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
### 7.2 Condicionales

La palabra clave if y su expresión condicional deben ir en la misma línea. Cuando exista un else o else if, la palabra clave else se escribe en su propia línea nueva, nunca compartiendo línea con la llave de cierre del bloque anterior.Esta regla diverge deliberadamente de la versión Java del estándar, donde else comparte línea con la llave de cierre (} else {). La configuración oficial de formato de C# que documenta Microsoft define como valor predeterminado que la palabra clave else inicie en una línea nueva, igual que ocurre con catch y finally (Microsoft, s. f.-a). Mantener esta regla alineada con el estilo Allman adoptado en 7.1 evita mezclar dos convenciones de llaves distintas dentro del mismo archivo.

**Con estándar**

```csharp
private const int MINIMUM_HEALTH = 0;

if (_currentHealth <= MINIMUM_HEALTH)
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
### 7.3 Bucles

La cláusula de inicialización de un bucle for no deberá declarar ni actualizar más de tres variables. Adicionalmente, el cuerpo de cualquier bucle que se ejecute con frecuencia dentro del ciclo de juego (por ejemplo, dentro de Update o FixedUpdate) deberá evitar operaciones que generen asignaciones de memoria en el heap (creación de objetos, cadenas o colecciones nuevas, consultas LINQ) en cada iteración.

El límite de variables en la cláusula de inicialización es una política de legibilidad propia del equipo, equivalente a la ya aplicada en la versión Java del estándar. La segunda parte de la regla sí responde a una recomendación documentada específicamente para Unity: el Manual de Unity explica que los tipos por referencia se alojan en el heap administrado y quedan sujetos al recolector de basura, y advierte que generar objetos temporales de forma repetida — su propio ejemplo ilustra esto con concatenaciones de cadenas dentro de un bucle — produce basura que eventualmente debe recolectarse, afectando el rendimiento (Unity Technologies, s. f.). Dado que un bucle dentro de `Update` puede ejecutarse decenas de veces por segundo, cualquier asignación evitable dentro de su cuerpo multiplica ese costo. Las estrategias concretas de reutilización de objetos (object pooling) se documentan en la sección 10.3.

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
### 7.4 Switch / switch expression

Todo switch deberá incluir una etiqueta default, incluso si su cuerpo queda vacío. Cada sección del switch que contenga al menos una instrucción debe terminar explícitamente con break, return, throw o goto case.

La etiqueta default obligatoria es una política de legibilidad propia del equipo, igual que en la versión Java del estándar. La segunda parte de la regla, en cambio, ya no es una convención de estilo sino un requisito impuesto por el propio compilador de C#: a diferencia de Java, donde omitir un break provoca que la ejecución continúe silenciosamente hacia el siguiente case, el compilador de C# genera el error CS0163 cuando una sección de un switch con instrucciones no termina de forma explícita, y exige usar goto case si realmente se desea continuar hacia la siguiente sección (Microsoft, s. f.-b). Esto significa que la regla del estándar Java sobre marcar con un comentario los fall through intencionales deja de aplicar en C# de la misma forma: el propio lenguaje obliga a declarar esa intención explícitamente, sin depender de un comentario que alguien podría omitir u olvidar actualizar.

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
        break;
    case GameState.Playing:
        ResumeGameplay();
        break;
}
```
### 7.5 Operador ternario

El operador ternario (condición ? valorSiVerdadero : valorSiFalso) solo podrá utilizarse cuando la condición sea una única expresión booleana simple, sin más de un operador lógico. Ambas ramas deben ser expresiones del mismo tipo que retornen un valor; no se permite invocar métodos void en ninguna rama. Se prohíbe anidar operadores ternarios.

Esta regla es una política de legibilidad propia del equipo, trasladada sin cambios de espíritu desde la versión Java del estándar. A nivel de lenguaje, C#  impone además una restricción que refuerza esta regla de forma estructural: ambas ramas del operador condicional deben poder convertirse a un tipo común, o el compilador rechaza la expresión, lo que en la práctica ya impide mezclar una rama que retorna un valor con otra que invoque un método void.

**Con estándar**

```csharp
string statusLabel = _isGameOver ? "Game Over" : "Playing";
```

**Sin estándar**

```csharp
string statusLabel = (_isGameOver && _livesRemaining <= 0 && !_isRespawning) ? "Game Over" : "Playing";
```

## 8. Manejo de errores y excepciones
### 8.1 Jerarquía de excepciones propias del dominio del juego

Las excepciones personalizadas deben derivar directamente de Exception (nunca de ApplicationException), terminar su nombre con el sufijo Exception, evitar jerarquías profundas, y proveer como mínimo los tres constructores estándar: sin parámetros, con mensaje, y con mensaje más excepción interna. Solo se crea un tipo de excepción nuevo cuando el código que captura necesita manejarla de forma distinta a las excepciones ya existentes.

La prohibición de heredar de ApplicationException y la exigencia de derivar directamente de Exception, evitando jerarquías profundas y usando el sufijo Exception, están documentadas en la guía de diseño de excepciones que forma parte de los mismos lineamientos de diseño de frameworks ya citados en la sección 5.5 (Cwalina et al., 2020). La página de referencia vigente de la propia clase ApplicationException confirma que esta recomendación se mantiene: Microsoft advierte ahí que las excepciones personalizadas deben derivarse de la clase Exception (Microsoft, s. f.-a). La exigencia de los tres constructores estándar, con los mismos nombres y tipos de parámetro en cada uno, está documentada en la guía vigente de buenas prácticas para excepciones de .NET (Microsoft, s. f.-c).

**Con estándar**

```csharp
public class SaveLoadException : Exception
{
    public SaveLoadException()
    {
    }

    public SaveLoadException(string message) : base(message)
    {
    }

    public SaveLoadException(string message, Exception innerException) : base(message, innerException)
    {
    }
}
```

**Sin estándar**

```csharp
public class SaveLoadException : ApplicationException
{
    public SaveLoadException()
    {
    }

    public SaveLoadException(string message) : base(message)
    {
    }

    public SaveLoadException(string message, Exception innerException) : base(message, innerException)
    {
    }
}
```
### 8.2 Try-catch y prohibición de catch vacíos

Los bloques catch nunca deben quedar vacíos. Debe capturarse el tipo de excepción más específico posible, no Exception o SystemException de forma genérica, y la excepción capturada debe manejarse, registrarse o volver a lanzarse envuelta en una excepción de dominio.

La prohibición de bloques catch vacíos se mantiene como política propia del equipo, por continuidad con la versión Java del estándar. La exigencia de capturar el tipo más específico posible sí corresponde a una regla de análisis de código vigente y numerada: CA1031 señala que las excepciones generales no deben capturarse, y que debe capturarse una excepción más específica o volver a lanzar la excepción general como última instrucción del bloque catch (Microsoft, s. f.-d).

**Con estándar**

```csharp
private void LoadCheckpoint(string checkpointPath)
{
    try
    {
        _saveData = SaveSerializer.Read(checkpointPath);
    }
    catch (IOException exception)
    {
        throw new SaveLoadException("Unable to load checkpoint file.", exception);
    }
}
```

**Sin estándar**

```csharp
private void LoadCheckpoint(string checkpointPath)
{
    try
    {
        _saveData = SaveSerializer.Read(checkpointPath);
    }
    catch (IOException exception)
    {
    }
}
```
### 8.3 Null-checking (?., ??, tipos de referencia anulables)

El proyecto habilita los tipos de referencia anulables (<Nullable>enable</Nullable>). Un campo o parámetro de tipo referencia que legítimamente puede estar ausente se declara con ? (por ejemplo, WeaponData? equippedWeapon), y se accede mediante los operadores ?. y ?? en lugar de comprobaciones explícitas de if (x != null) cuando sea posible.

Los tipos de referencia anulables reducen la probabilidad de que el código lance una System.NullReferenceException: el desarrollador declara qué variables pueden contener null, y el compilador advierte cuando el uso del código no coincide con esa declaración, sin alterar el comportamiento en tiempo de ejecución del programa (Microsoft, s. f.-e). Esta característica está desactivada por defecto y se controla a nivel de proyecto mediante la configuración de compilación (Microsoft, s. f.-f). Declarar explícitamente qué campos pueden estar ausentes, en lugar de tratarlos como implícitamente anulables, sustituye en C# el uso de Optional<T> de la versión Java del estándar.

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
### 8.4 Guard clauses / validación temprana de parámetros

Todo método público valida sus parámetros de tipo referencia como primera instrucción del cuerpo del método, antes de usarlos para cualquier otro propósito, lanzando inmediatamente mediante ArgumentNullException.ThrowIfNull (u otro método Throw... equivalente).

ArgumentNullException.ThrowIfNull, disponible desde .NET 6, valida un argumento y lanza ArgumentNullException si es null, infiriendo automáticamente el nombre del parámetro sin necesidad de pasarlo de forma explícita (Microsoft, s. f.-b). Colocar esta validación como primera instrucción del método es lo que distingue una validación temprana real de una tardía: si la comprobación ocurre después de que el parámetro ya fue utilizado, parte del daño potencial de recibir un valor inválido pudo haber ocurrido antes de que la excepción se lance.

**Con estándar**

```csharp
public void EquipWeapon(WeaponData weapon)
{
    ArgumentNullException.ThrowIfNull(weapon);

    _equippedWeapon = weapon;
}
```

**Sin estándar**

```csharp
public void EquipWeapon(WeaponData weapon)
{
    _equippedWeapon = weapon;

    ArgumentNullException.ThrowIfNull(weapon);
}
```

## 9. Complejidad
### 9.1 Números mágicos
### 9.2 Complejidad ciclomática máxima
### 9.3 Número máximo de parámetros por método
### 9.4 Número máximo de operadores lógicos por expresión

## 10. Prácticas específicas de C# / Unity
### 10.1 Propiedades vs. campos públicos
### 10.2 Uso de LINQ (restricciones por rendimiento en bucles de juego)
### 10.3 Cacheo de referencias y Object Pooling
### 10.4 ScriptableObjects para datos/configuración
### 10.5 Serialización ([SerializeField], [System.Serializable])
### 10.6 Eventos (UnityEvent, event, Action)
### 10.7 Structs vs. classes vs. records (posiciones, stats, DTOs de guardado)

## 11. Comentarios y documentación

Todo fragmento de código que se desvíe de una norma del estándar, que implemente una decisión de diseño no evidente o que resuelva un caso especial deberá estar acompañado de un comentario que explique el motivo de dicha decisión, no únicamente lo que hace el código. Los comentarios se escriben en inglés, por consistencia con el resto del código fuente.
### 11.1 Comentarios de bloque
### 11.2 Comentarios de línea

Los comentarios de una sola línea (`//`) inician con mayúscula, terminan con punto y llevan un espacio entre `//` y el texto. Se colocan en su propia línea, precedidos por una línea en blanco cuando aportan claridad; no se colocan al final de una línea de código.

Esta regla diverge deliberadamente de la versión Java del estándar, que sí permitía el comentario al final de la línea. La convención oficial de C# que documenta Microsoft es explícita en los cuatro puntos: el comentario se coloca en una línea separada y no al final de una línea de código, inicia con mayúscula, termina con punto, y lleva un espacio después del delimitador (Microsoft, s. f.-a).

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
### 11.3 Comentarios de documentación XML (///)

Todo miembro público (clases, métodos, propiedades) debe documentarse con comentarios de documentación XML (`///`), como mínimo con la etiqueta `<summary>`, y con una etiqueta `<param>` por cada parámetro. Estos comentarios se colocan inmediatamente arriba del elemento que documentan, sin línea en blanco entre ambos.

Los comentarios de documentación XML, delimitados por triple diagonal (`///`) y colocados directamente antes del bloque de código al que describen, son el mecanismo oficial de C# para documentación de API, y el compilador puede generar un archivo de documentación a partir de ellos mediante la opción `GenerateDocumentationFile` (Microsoft, s. f.-b). La misma fuente señala que, si esta opción está habilitada, el compilador emite la advertencia CS1591 para cualquier miembro público sin comentario de documentación, lo que en la práctica hace de esta regla algo verificable automáticamente por el propio compilador. A diferencia del comentario de bloque de la sección 11.1, no puede existir una línea en blanco entre el comentario `///` y el miembro que documenta: el compilador asocia el comentario con el elemento inmediatamente posterior, por lo que una línea en blanco de por medio deja al miembro sin documentación asociada, aunque el texto siga presente en el archivo.

**Con estándar**
```csharp
/// <summary>
/// Applies damage to the player and triggers defeat once health reaches the minimum threshold.
/// </summary>
/// <param name="amount">The amount of damage to apply.</param>
public void ApplyDamage(int amount)
{
    _currentHealth -= amount;
}
```

**Sin estándar**
```csharp
/// <summary>
/// Applies damage to the player and triggers defeat once health reaches the minimum threshold.
/// </summary>
/// <param name="amount">The amount of damage to apply.</param>

public void ApplyDamage(int amount)
{
    _currentHealth -= amount;
}
```
### 11.4 Comentarios especiales (TODO, FIXME)

`TODO` marca funcionalidad pendiente de implementar; `FIXME` marca un comportamiento incorrecto conocido que debe corregirse. Ambos se escriben en mayúsculas, se colocan inmediatamente antes de la sección de código correspondiente, y deben ir acompañados de una descripción clara del pendiente. Todo comentario `TODO` o `FIXME` debe resolverse antes de la entrega final.

`TODO` es uno de los tokens que Visual Studio reconoce de forma nativa y añade automáticamente a la ventana Task List para dar seguimiento a pendientes dentro del código (Microsoft, s. f.-c). Cabe aclarar una diferencia entre plataformas: los tokens predeterminados de Visual Studio para Windows son `HACK`, `TODO`, `UNDONE` y `UnresolvedMergeConflict` —`FIXME` no está incluido por defecto y debe añadirse como token personalizado—, mientras que Visual Studio para Mac sí incluye `FIXME` entre sus tokens predeterminados. El equipo mantiene `FIXME` como token del estándar, junto a `TODO`, por continuidad con la versión Java; quienes usen Visual Studio en Windows deberán agregarlo manualmente como token personalizado para que aparezca en su Task List.

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

## 12. Manejo de logs y categorización de errores
### 12.1 Sistema/herramienta de logging
### 12.2 Niveles de log: Trace, Debug, Info, Warning, Error
### 12.3 Criterio de aplicación por nivel (contexto de juego)
### 12.4 Formato del mensaje
### 12.5 Logs en editor vs. build final

> *Nota: aquí falta decidir qué tecnologías vamos a usar.*

## 13. Gestión de escenas y UI
### 13.1 Navegación entre escenas (SceneManager centralizado)
### 13.2 Mensajes/feedback al jugador (HUD, popups, pantallas de carga)

## 14. Validación de entradas y seguridad
### 14.1 Validación de inputs del jugador
### 14.2 Autoridad del servidor (si el proyecto es multijugador)
### 14.3 Manejo de datos sensibles
### 14.4 Persistencia de partidas (save/load) e integridad de datos

## 15. Pruebas unitarias
### 15.1 Framework y ubicación (EditMode / PlayMode)
### 15.2 Nomenclatura de métodos de prueba
### 15.3 Estructura Arrange-Act-Assert
### 15.4 Un assert por test
### 15.5 Mocking de dependencias (interfaces + NSubstitute/Moq)
### 15.6 Métodos builder para objetos de prueba complejos

## 16. Dependencias externas
### 16.1 Librerías/paquetes utilizados
### 16.2 Vulnerabilidades conocidas (formato CVE, aplica/no aplica)

## 17. Referencias

- Microsoft. (s. f.-a). *C# formatting options*. Microsoft Learn. Recuperado el 18 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options
- Microsoft. (s. f.-b). *Compiler Error CS0163*. Microsoft Learn. Recuperado el 18 de agosto de 2026, de https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/compiler-messages/cs0163
- Unity Technologies. (s. f.). *Garbage collection best practices*. Unity Manual. Recuperado el 18 de agosto de 2026, de https://docs.unity3d.com/2022.2/Documentation/Manual/performance-garbage-collection-best-practices.html