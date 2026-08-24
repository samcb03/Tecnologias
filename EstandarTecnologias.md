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
16. [Referencias](#16-referencias)

<div style="page-break-after: always;"></div>

## 1. Introducción

En este documento se definen las reglas a seguir para el desarrollo de nuestro proyecto de videojuego, tomando como base las convenciones oficiales “Microsoft C# Coding Conventions” que aseguran consistencia en el código, con el fin de que sea fácil de leer, entender y de mantener para cualquier miembro del equipo, además de unificar el formato para evitar problemas. Este estándar además de cubrir que el código se vea estético, sino también reglas de estructuras  que nos permitirán integrar las mecánicas en un producto final estable y unificado.

### 1.1 Problemática

El desarrollo de un videojuego en un entorno escolar empleando buenas prácticas, así como también se busca que sea multijugador, empleando conocimientos de cursos anteriores, siendo conocimiento acumulativo.

### 1.2 Propósito

Se busca garantizar que el desarrollo del videojuego cumpla con los pilares de calidad necesarios para un producto final estable:
- `Mantenibilidad`: asegurar que la arquitectura sea legible, escalable y comprensible para cualquier desarrollador del equipo, preservando su integridad técnica a largo plazo.
- `Detección temprana de errores`: facilitar la identificación de inconsistencias o desviaciones del estándar durante las revisiones de código, mitigando riesgos antes de las fases de entrega.
- `Productividad`: optimizar el flujo de trabajo al unificar criterios de formato, permitiendo que el equipo priorice la resolución de mecánicas y lógica de diseño sobre debates estéticos.
- `Rendimiento consistente`: garantizar que las convenciones de estilo no comprometan la eficiencia del ciclo de ejecución, especialmente en procesos críticos que impactan los cuadros por segundo.


### 1.3 Idioma del código

El código fuente (nombres de clases, métodos, variables, constantes y comentarios) se escribe en inglés. Esta regla aplica específicamente al código fuente; las convenciones para otros elementos del proyecto (textos de interfaz, base de datos, mensajes de commit) se abordan en sus secciones correspondientes.
Las guías de nombrado de Microsoft para C# incluyen, dentro de sus convenciones generales, una recomendación específica sobre evitar nombres de identificadores ligados a un idioma en particular (Microsoft, s. f.). Escribir el código en inglés, en lugar de español, hace que sea comprensible para cualquier desarrollador que lo revise en el futuro, independientemente de su idioma nativo, y mantiene el código consistente con el idioma en el que están documentadas tanto la API de C# como la de Unity que el equipo consulta constantemente.

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

Los identificadores deberán escribirse en inglés y describir claramente su propósito. Se priorizará la claridad sobre la brevedad y se evitarán abreviaturas, palabras reservadas y nombres de un solo carácter. Se permitirán identificadores de una letra únicamente en contadores de ciclos, excepciones capturadas y parámetros de eventos cuando su alcance sea menor o igual a tres líneas. También se permitirá el parámetro `e` cuando forme parte de la firma convencional de un manejador de eventos.

No se utilizarán dos guiones bajos consecutivos, ya que estos nombres están reservados para identificadores generados por el compilador.

C# utiliza principalmente:

- `PascalCase` para clases, estructuras, interfaces, métodos, propiedades, eventos, constantes y espacios de nombres.
- `camelCase` para variables locales y parámetros.
- `_camelCase` para campos de instancia privados o internos.
- `s_camelCase` para campos estáticos privados o internos.

Estas reglas corresponden a las convenciones oficiales para identificadores de C# (Microsoft, 2026b).

### 4.1 Variables y parámetros

Las variables locales y los parámetros deberán escribirse utilizando `camelCase`. Sus nombres deberán ser sustantivos o frases nominales que permitan comprender qué información almacenan.

Se evitarán nombres de un solo carácter, excepto en contadores de ciclos simples como `i`, `j` o `k`, en excepciones capturadas como `e` y en parámetros de eventos convencionales, siempre que su alcance sea menor o igual a tres líneas.

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

### 4.2 Colecciones

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

### 4.3 Booleanos

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

### 4.4 Declaración y sombreado de variables

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

### 4.5 Campos privados e internos

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

### 4.6 Propiedades

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

Las propiedades booleanas deberán expresar condiciones afirmativas y las propiedades de colecciones deberán utilizar nombres en plural. Estas recomendaciones aparecen en las convenciones oficiales para miembros de tipos (Microsoft, 2023).

### 4.7 Constantes

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

### 4.8 Métodos

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

### 4.9 Eventos

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

Los métodos protegidos que disparen un evento deberán comenzar con `On`, seguido del nombre del evento. Los parámetros de un manejador de eventos deberán llamarse `sender` y `e`, de acuerdo con las convenciones oficiales para miembros de tipos de .NET (Microsoft, 2023).

### 4.10 Métodos de prueba unitaria

Los métodos de prueba deberán utilizar el siguiente formato:

```csharp
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

Las partes `NombreMetodo`, `Flujo` y `Resultado` coinciden con las prácticas recomendadas por Microsoft para nombrar pruebas unitarias. El prefijo `Test` es una convención propia del equipo (Microsoft, 2025b).

### 4.11 Clases, estructuras y registros

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

### 4.12 Interfaces

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

Las reglas para clases e interfaces están recogidas en las guías oficiales de diseño de .NET (Microsoft, 2025e).

### 4.13 Parámetros de tipo genérico

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

### 4.14 Enumeraciones

Los nombres de las enumeraciones y sus valores deberán escribirse utilizando `PascalCase`.

Las enumeraciones normales deberán utilizar un nombre singular. Las enumeraciones que representen una combinación de indicadores deberán utilizar un nombre plural. No se agregarán los sufijos `Enum`,`Flag` o `Flags`.

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

Los espacios de nombres deberán utilizar `PascalCase`. Sus componentes se separarán mediante puntos y deberán representar de forma clara el proyecto y la funcionalidad agrupada.

**Con estándar**

```csharp
namespace CompanyName.GameName.Combat;
```

**Sin estándar**

```csharp
namespace company_name.game_name.combat;
```

### 4.16 Sufijos oficiales por responsabilidad

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

## 5 Estilo de código

El código deberá mantener un formato uniforme que facilite su lectura, revisión y mantenimiento. Las reglas de esta sección se aplicarán a todos los archivos.

Se utilizarán cuatro espacios para la indentación, llaves con estilo Allman, una instrucción por línea y líneas de continuación indentadas. Estas reglas toman como base las convenciones de código oficiales de C# (Microsoft, 2025d).

### 5.1 Formato general (indentación, límite de columnas)

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
    selectedDifficulty,
    currentLevel,
    battleRules);
```

**Sin estándar**

```csharp
BattleResult battleResult = battleService.ResolveBattle(selectedDifficulty, currentLevel, battleRules);
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
    initialHealth);
```

**Sin estándar**

```csharp
Enemy enemy = enemyFactory.Create(enemyType,
    spawnPosition, initialHealth);
```

### 5.2 Espacios en blanco (vertical/horizontal)

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

Se colocará un espacio a cada lado de los operadores binarios, como `=`, `+`, `-`,`==`, `!=`, `&&` y `||`.

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

### 5.3 Organización del archivo (orden de `using`)

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

### 5.4 Orden de miembros de la clase

Los miembros de una clase deberán conservar el siguiente orden general:

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

Las propiedades deberán colocarse después de los eventos y antes de los métodos.

**Con estándar**

```csharp
public int CurrentHealth { get; private set; }

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

public int CurrentHealth { get; private set; }
```

**Orden de métodos según su visibilidad**

Después de las propiedades se colocarán primero los métodos públicos, después los protegidos y finalmente los privados.

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

## 6. Estructuras de control

### 6.1 Llaves

El uso de llaves será obligatorio en la totalidad de las estructuras de control (if, else, for, while, do-while, switch), sin excepción para bloques que contengan una única instrucción.

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

La palabra clave `if` y su expresión condicional deben ir en la misma línea. Cuando exista un `else` o `else if`, la palabra clave `else` se escribirá en su propia línea, nunca compartiendo línea con la llave de cierre del bloque anterior.

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

La cláusula de inicialización de un bucle `for` no deberá declarar ni actualizar más de tres variables. Adicionalmente, un bucle que se ejecute una vez por cuadro o con alta frecuencia deberá evitar operaciones que creen objetos, cadenas o colecciones nuevas en cada iteración cuando esas asignaciones puedan reutilizarse.

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

Toda sentencia `switch` deberá incluir una etiqueta `default`. Cada sección con instrucciones deberá terminar explícitamente con `break`, `return`, `throw`. La etiqueta `default` obligatoria es una política de legibilidad del equipo.

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

El operador ternario (condición ? valorSiVerdadero : valorSiFalso) solo podrá utilizarse cuando la condición sea una única expresión booleana simple, sin más de un operador lógico. Ambas ramas deben ser expresiones del mismo tipo que retornen un valor; no se permite invocar métodos void en ninguna rama. Se prohíbe anidar operadores ternarios.

**Con estándar**

```csharp
string statusLabel = _isGameOver ? "Game Over" : "Playing";
```

**Sin estándar**

```csharp
string statusLabel = (_isGameOver && _livesRemaining <= 0 && !_isRespawning) ? "Game Over" : "Playing";
```

## 7. Manejo de errores y excepciones

### 7.1 Jerarquía de excepciones propias del dominio del juego

Las excepciones personalizadas deben derivar directamente de Exception, terminar su nombre con el sufijo Exception, evitar jerarquías profundas, y proveer como mínimo los tres constructores estándar: sin parámetros, con mensaje, y con mensaje más excepción interna. Solo se crea un tipo de excepción nuevo cuando el código que captura necesita manejarla de forma distinta a las excepciones ya existentes.

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

    public SaveLoadException(string message, Exception innerException) : base(message, innerException)
    {
    }
}
```

### 7.2 Try-catch y prohibición de catch vacíos

Los bloques `catch` nunca deberán quedar vacíos. Se capturará el tipo de excepción más específico posible. La excepción capturada deberá manejarse, registrarse, volver a lanzarse mediante `throw;` o envolverse en una excepción de dominio que conserve la excepción original como excepción interna.

Solo se permitirá capturar `Exception` o `SystemException` en un límite claramente definido de la aplicación y cuando el bloque termine volviendo a lanzar la excepción mediante `throw;`.

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

### 7.3 Null-checking (?., ??, tipos de referencia anulables)

El proyecto habilita los tipos de referencia anulables (\<Nullable>enable\</Nullable>). Un campo o parámetro de tipo referencia que legítimamente puede estar ausente se declara con ? (por ejemplo, WeaponData? equippedWeapon), y se accede mediante los operadores ?. y ?? en lugar de comprobaciones explícitas de if (x != null) cuando sea posible.

Los tipos de referencia anulables permiten declarar qué variables pueden contener `null` y hacen que el compilador advierta cuando el uso del código no coincide con esa declaración, sin alterar el comportamiento en tiempo de ejecución. El contexto anulable se habilita mediante la opción `<Nullable>enable</Nullable>` del proyecto (Microsoft, 2024).

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

## 8. Complejidad

La gestión de la complejidad en el código fuente es un pilar fundamental para asegurar la mantenibilidad, escalabilidad y la detección temprana de defectos en el desarrollo de software (Martin, 2008). En el contexto del desarrollo de videojuegos, donde los bucles lógicos se ejecutan decenas de veces por segundo, mantener una baja complejidad reduce drásticamente los cuellos de botella en el procesamiento y facilita la creación de pruebas unitarias efectivas.

### 8.1 Números mágicos

Se prohíbe el uso de literales numéricos (distintos de 0, 1 y -1 cuando se usan como valores triviales de inicialización, incremento o comparación de signo) directamente dentro de una expresión o instrucción. Todo valor numérico con significado de negocio (umbrales de vida, cantidades de inventario, tiempos de spawn, identificadores de slot) debe declararse como una constante (const) o un campo de solo lectura (static readonly con un nombre descriptivo que exprese su propósito.


**Con estándar**

```csharp
public class HealthSystem
{
    private const int MaxHealth = 100;
    private const int LowHealthThreshold = 20;

public bool IsLowHealth(int currentHealth) {
        return currentHealth <= LowHealthThreshold;
    }
}
```

**Sin estándar**

```csharp
public class HealthSystem
{

public bool IsLowHealth(int currentHealth) {
        return currentHealth <= 20;
    }
}
```

### 8.2 Complejidad ciclomática máxima

Ningún método podrá superar una complejidad ciclomática de 10, medida como el número de caminos linealmente independientes en su grafo de flujo de control. 

**Con estándar**

```csharp
public class CombatResolver
{
    private const int NoDamage = 0;
    private const int CriticalHitThreshold = 3;
    private const int CriticalDamageMultiplier = 2;

    public int ResolveAttack(Attacker attacker, Defender defender, WeaponData weapon)
    {
        var finalDamage = NoDamage;

        if (CanAttack(attacker, defender))
        {
            var baseDamage = CalculateBaseDamage(attacker, weapon);
            var reducedDamage = ApplyDefense(baseDamage, defender);
            finalDamage = ApplyCriticalModifier(reducedDamage, attacker.CriticalRolls);
        }

        return finalDamage;
    }

    private bool CanAttack(Attacker attacker, Defender defender)
    {
        var canAttack = attacker.IsAlive
            && defender.IsAlive
            && attacker.HasStamina;

        return canAttack;
    }

    private int CalculateBaseDamage(Attacker attacker, WeaponData weapon)
    {
        var baseDamage = attacker.Strength * weapon.DamageMultiplier;

        return baseDamage;
    }

    private int ApplyDefense(int rawDamage, Defender defender)
    {
        var reducedDamage = rawDamage - defender.Armor;
        var finalDamage = Mathf.Max(reducedDamage, NoDamage);

        return finalDamage;
    }

    private int ApplyCriticalModifier(int damage, int criticalRolls)
    {
        var finalDamage = damage;

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

Todo método podrá recibir como máximo tres parámetros. Cuando la operación requiera más datos de entrada, estos deberán agruparse en un tipo dedicado (struct o class según corresponda por la sección 10.7 de este estándar), en lugar de ampliar la firma del método.

 McConnell (2004) reporta que las firmas de método extensas dificultan tanto la lectura en el punto de llamada como la comprobación del orden correcto de los argumentos, y recomienda agrupar parámetros relacionados en un objeto propio cuando su número crece. 

**Con estándar**

```csharp
public Enemy Spawn(EnemySpawnRequest request)
{
    var enemy = enemyFactory.Create(request.Type, request.Position);
    enemy.Configure(request.Level, request.Faction);
    return enemy;
}
```

**Sin estándar**

```csharp
public Enemy Spawn(EnemyType type, float positionX, float positionY, float positionZ, int level, Faction faction)
{
    var enemy = enemyFactory.Create(type, positionX, positionY, positionZ);
    enemy.Configure(level, faction);
    return enemy;
}
```

### 8.4 Número máximo de operadores lógicos por expresión

Ninguna expresión condicional podrá contener más de tres operadores lógicos o de comparación (&&, ||, ==, !=, <, >, <=, >=) combinados en una misma línea. Cuando una condición requiera evaluar más criterios, estos deberán descomponerse en variables booleanas intermedias con nombre descriptivo.

**Con estándar**

```csharp
public class SaveSystem
{
    private const int MinimumProgressPercent = 5;

    public bool CanSaveGame(PlayerState state, LevelState level)
    {
        var hasMinimumProgress = level.ProgressPercent >= MinimumProgressPercent;
        var isInSafeZone = level.CurrentZone.IsSafe;
        var isPlayerAlive = state.IsAlive;
        var isNotInCutscene = !level.IsPlayingCutscene;

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

## 9. Prácticas específicas de C#

### 9.1 Propiedades vs. campos públicos

### 9.2 Uso de LINQ (restricciones en rutas de ejecución frecuentes)

### 9.3 Reutilización de referencias y Object Pooling

### 9.4 Objetos para datos y configuración

### 9.5 Serialización (`[System.Serializable]` y serializador seleccionado)

### 9.6 Eventos (`event`, `EventHandler` y `Action`)

### 9.7 Structs vs. classes vs. records (posiciones, stats, DTOs de guardado)

## 10. Comentarios y documentación

Todo fragmento de código que se desvíe de una norma del estándar, que implemente una decisión de diseño no evidente o que resuelva un caso especial deberá estar acompañado de un comentario que explique el motivo de dicha decisión, no únicamente lo que hace el código. Los comentarios se escriben en inglés, por consistencia con el resto del código fuente.

### 10.1 Comentarios de bloque

Los comentarios de bloque (`/* ... */`) se utilizarán de manera excepcional cuando una justificación necesite conservarse como un bloque breve de varias líneas. Se colocarán antes del código al que se refieren, precedidos por una línea en blanco y al mismo nivel de indentación. Cuando una sola línea sea suficiente, se utilizará el formato `//` definido en 10.2.

Los comentarios de bloque nunca deberán utilizarse para construir separadores decorativos mediante líneas de asteriscos.

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

Los comentarios de una sola línea (`//`) inician con mayúscula, terminan con punto y llevan un espacio entre `//` y el texto. Se colocan en su propia línea, precedidos por una línea en blanco cuando aportan claridad; no se colocan al final de una línea de código.

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

Todo tipo o miembro que forme parte de la API pública del código de producción deberá documentarse con comentarios de documentación XML (`///`), como mínimo con la etiqueta `<summary>` y con una etiqueta `<param>` por cada parámetro. Estos comentarios se colocarán inmediatamente arriba del elemento que documentan, sin una línea en blanco entre ambos.

Las clases y los métodos de los proyectos de prueba estarán exentos, salvo que el equipo decida documentarlos. Los fragmentos del presente estándar también podrán omitir la documentación XML cuando la regla ilustrada no sea la documentación. Esta excepción evita que los ejemplos marcados como “Con estándar” contradigan esta sección.

Los comentarios `///` son el mecanismo oficial de C# para documentar una API. Cuando se habilita `GenerateDocumentationFile`, el compilador genera la advertencia CS1591 para los miembros públicamente visibles que no tengan documentación XML (Microsoft, 2026e).

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

### 10.4 Comentarios especiales (TODO, FIXME)

`TODO` marca funcionalidad pendiente de implementar; `FIXME` marca un comportamiento incorrecto conocido que debe corregirse. Ambos se escriben en mayúsculas, se colocan inmediatamente antes de la sección de código correspondiente, y deben ir acompañados de una descripción clara del pendiente. Todo comentario `TODO` o `FIXME` debe resolverse antes de la entrega final.

El reconocimiento automático de estos tokens dependerá del editor utilizado. La obligación de resolverlos antes de la entrega se mantiene independientemente de que el editor los muestre en una lista de tareas.

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

El registro de eventos (logging) es el mecanismo principal para diagnosticar el comportamiento de un videojuego una vez que ya no se está depurando paso a paso dentro del editor, especialmente en sistemas que se ejecutan por frame (spawn de enemigos, resolución de combate) o que involucran persistencia (guardado de partida). Esta sección regula la herramienta de logging a utilizar, los niveles disponibles, el criterio para elegir cada nivel, el formato del mensaje y la diferencia de comportamiento entre el editor y el build final.

### 11.1 Sistema/herramienta de logging

Queda prohibido escribir a la salida estándar o a cualquier destino de registro directamente desde la lógica de gameplay. Todo registro debe pasar por una clase centralizada GameLogger, que expone un método por nivel y delega la escritura real a una implementación de ILogSink inyectada (consola, archivo u otro destino, según el entorno de ejecución). Ningún componente fuera de GameLogger puede escribir un log directamente.

**Con estándar**

```csharp
public void SaveGame(PlayerState state)
{
    GameLogger.Info(nameof(SaveSystem), "Guardado de partida iniciado");
    PersistToDisk(state);
}
```

**Sin estándar**

```csharp
public void SaveGame(PlayerState state)
{
    Console.WriteLine("Guardado de partida iniciado");
    PersistToDisk(state);
}
```

### 11.2 Niveles de log: Trace, Debug, Info, Warning, Error

GameLogger deberá exponer exactamente cinco niveles, ordenados de menor a mayor severidad: Trace, Debug, Info, Warning y Error. No se permite introducir niveles adicionales ni usar un nivel para un propósito distinto al definido en 12.3.

Chuvakin et al. (2013) describen la jerarquía de niveles de severidad como el mecanismo estándar de la industria para permitir que un mismo sistema de logging sirva tanto para depuración detallada en desarrollo como para monitoreo de incidentes en producción, filtrando por nivel según el contexto de ejecución sin cambiar el código fuente.g.

**Con estándar**

```csharp
public enum LogLevel
{
    Trace,
    Debug,
    Info,
    Warning,
    Error
}
```

**Sin estándar**

```csharp
public enum LogLevel
{
    Verbose,
    Info,
    Oops,
    Critical
}
```

### 11.3 Criterio de aplicación por nivel (contexto de juego)

Cada nivel deberá reservarse para el siguiente tipo de evento:

- `Trace`: eventos de muy alta frecuencia usados solo para depuración fina (posición del jugador en cada ciclo de actualización, cada iteración de un bucle de física).
- `Debug`: información de desarrollo no crítica (valores intermedios de una fórmula de daño, estado de una máquina de estados de un enemigo).
- `Info`: hitos normales del flujo del juego (partida guardada correctamente, jugador entra a un nuevo nivel, enemigo generado por el EnemySpawner).
- `Warning`: situaciones anómalas pero recuperables (intento de recoger un objeto con el inventario lleno, archivo de guardado con una versión antigua pero migrable).
- `Error`: fallos que impiden completar una operación crítica (fallo de escritura del archivo de guardado, referencia nula a los datos requeridos para el spawn).

**Con estándar**

```csharp
if (items.Count >= MaxSlots)
{
    GameLogger.Warning(nameof(InventorySystem), "Inventario lleno, no se pudo agregar el objeto");
    return false;
}
```

**Sin estándar**

```csharp
if (items.Count >= MaxSlots)
{
    GameLogger.Error(nameof(InventorySystem), "no se pudo agregar el objeto");
    return false;
}
```

### 11.4 Formato del mensaje

Todo mensaje de log deberá construirse con la firma GameLogger.<Nivel>(categoria, mensaje), donde categoria es el nombre de la clase de origen (obtenido con nameof) y mensaje describe el evento en español, sin concatenar valores dinámicos mediante el operador +. Cuando el mensaje deba incluir un valor variable, este se pasará como argumento adicional a un método sobrecargado que use string.Format internamente, nunca interpolación ni concatenación directa en el punto de la llamada.

Chuvakin et al. (2013) recomiendan un formato de mensaje consistente y con estructura fija (nivel, origen, contenido) para que los logs puedan procesarse de forma automática por herramientas externas, en lugar de depender de texto libre. McConnell (2004) advierte que construir cadenas mediante concatenación en cada llamada de diagnóstico añade trabajo de asignación de memoria incluso cuando el nivel de log correspondiente está deshabilitado.

**Con estándar**

```csharp
GameLogger.Info(nameof(EnemySpawner), "Enemigo generado: {0}", request.Type);
```

**Sin estándar**

```csharp
Console.WriteLine("Enemigo generado: " + request.Type.ToString());
```

### 11.5 Logs en entornos de desarrollo y versiones finales

Los niveles Trace y Debug deberán compilarse únicamente en builds de desarrollo, usando el atributo [System.Diagnostics.Conditional("DEBUG")] sobre los métodos correspondientes de GameLogger, de forma que las llamadas se eliminen por completo del build final en lugar de evaluarse y descartarse en tiempo de ejecución. Los niveles Info, Warning y Error sí deberán persistir en el build final.

**Con estándar**

```csharp
[System.Diagnostics.Conditional("DEBUG")]
public static void Trace(string category, string message)
{
    sink.Write(LogFormatter.Format(LogLevel.Trace, category, message));
}
```

**Sin estándar**

```csharp
public static void Trace(string category, string message)
{
    if (BuildConfiguration.IsDebug)
    {
        sink.Write(LogFormatter.Format(LogLevel.Trace, category, message));
    }
}
```

## 12. Gestión de estados, pantallas y UI

### 12.1 Navegación centralizada entre estados o pantallas

### 12.2 Mensajes/feedback al jugador (HUD, popups, pantallas de carga)

## 13. Validación de entradas y seguridad

### 13.1 Validación de inputs del jugador

### 13.2 Autoridad del servidor (si el proyecto es multijugador)

### 13.3 Manejo de datos sensibles

### 13.4 Persistencia de partidas (save/load) e integridad de datos

## 14. Pruebas unitarias

Las pruebas unitarias deberán verificar comportamientos individuales del código de manera rápida, aislada, repetible y automática. No deberán depender de archivos reales, conexiones externas, servicios remotos, fechas del sistema ni otros recursos que puedan producir resultados variables.

Las pruebas se escribirán utilizando NUnit como framework de referencia. Las dependencias podrán sustituirse mediante NSubstitute o Moq, pero el equipo deberá seleccionar una sola biblioteca de mocking y utilizarla consistentemente en todo el proyecto.

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

Las pruebas unitarias y las pruebas de integración deberán almacenarse en proyectos o ensamblados separados.

Las pruebas unitarias se colocarán en `tests/AdventureGame.Tests.Unit`. Las pruebas de integración se colocarán en `tests/AdventureGame.Tests.Integration`.

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

Las clases que prueben lógica aislada, cálculos, validaciones, reglas de combate o transformaciones de datos deberán colocarse dentro del proyecto de pruebas unitarias.

**Con estándar**

```csharp
tests/AdventureGame.Tests.Unit/Combat/DamageCalculatorTests.cs
```

**Sin estándar**

```csharp
tests/AdventureGame.Tests.Integration/Combat/DamageCalculatorTests.cs
```

**Ubicación de pruebas de integración**

Las pruebas que utilicen archivos reales, bases de datos, servicios externos o varios componentes concretos deberán colocarse dentro del proyecto de pruebas de integración.

**Con estándar**

```csharp
tests/AdventureGame.Tests.Integration/Saving/FileSaveGameRepositoryTests.cs
```

**Sin estándar**

```csharp
tests/AdventureGame.Tests.Unit/Saving/FileSaveGameRepositoryTests.cs
```

**Correspondencia entre archivos y clases de prueba**

Cada archivo deberá contener una sola clase de prueba. El nombre del archivo deberá coincidir con el nombre de la clase.

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

### 14.2 Nomenclatura de métodos de prueba

**Nomenclatura de las clases de prueba**

El nombre de una clase de prueba deberá formarse con el nombre de la clase probada y el sufijo `Tests`.

**Con estándar**

```csharp
public sealed class DamageCalculatorTests
{
}
```

**Sin estándar**

```csharp
public sealed class DamageTests
{
}
```

**Estructura del nombre del método de prueba**

Los métodos de prueba deberán seguir la estructura:

`Test_NombreMetodo_Flujo_Resultado`

El nombre deberá contener:

1. El prefijo `Test`.
2. El nombre del método probado.
3. El flujo o escenario evaluado.
4. El resultado esperado.

Microsoft recomienda que los nombres de las pruebas indiquen el método probado, el escenario y el comportamiento esperado. El prefijo `Test` se conserva como convención propia del equipo (Microsoft, 2025b).

**Con estándar**

```csharp
[Test]
public void Test_CalculateDamage_EnemyWithoutDefense_ReturnsAttackPower()
{
}
```

**Sin estándar**

```csharp
[Test]
public void DamageTest()
{
}
```

**Idioma y capitalización**

Los nombres de las pruebas deberán escribirse en inglés. Cada parte del nombre deberá utilizar `PascalCase` y separarse mediante un guion bajo.

**Con estándar**

```csharp
[Test]
public void Test_RestoreHealth_PlayerIsDamaged_RestoresMaximumHealth()
{
}
```

**Sin estándar**

```csharp
[Test]
public void test_restaurarvida_jugadorDañado_funciona()
{
}
```

**Descripción del flujo**

El flujo deberá describir la condición específica bajo la cual se ejecuta el método. No se utilizarán palabras genéricas como `Valid`, `Normal` o `Works` cuando exista una descripción más precisa.

**Con estándar**

```csharp
[Test]
public void Test_UseItem_InventoryIsEmpty_ReturnsFalse()
{
}
```

**Sin estándar**

```csharp
[Test]
public void Test_UseItem_Normal_Works()
{
}
```

**Descripción del resultado**

La última parte del nombre deberá indicar el resultado observable esperado mediante expresiones como `Returns`, `Throws`, `Adds`, `Removes`, `Updates` o `DoesNotChange`.

**Con estándar**

```csharp
[Test]
public void Test_AddExperience_ExperienceReachesLimit_AddsLevel()
{
}
```

**Sin estándar**

```csharp
[Test]
public void Test_AddExperience_ExperienceReachesLimit_ValidResult()
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

### 14.3 Estructura Arrange-Act-Assert

Cada prueba deberá seguir el patrón Arrange-Act-Assert:

1. **Arrange:** crea y configura los datos, dependencias y objeto probado.
2. **Act:** ejecuta una sola operación sobre el objeto probado.
3. **Assert:** comprueba un único resultado observable.

Las tres etapas deberán separarse mediante una línea en blanco. No será necesario agregar comentarios `// Arrange`, `// Act` y `// Assert` cuando la separación y los nombres hagan evidente la estructura.

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

La etapa Arrange deberá contener únicamente la creación y configuración necesarias para el comportamiento probado. No se configurarán propiedades o dependencias que no influyan en el resultado.

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

La etapa Act deberá contener una sola operación principal. Si una prueba necesita ejecutar varias acciones independientes, deberá dividirse en pruebas separadas.

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

La operación probada no deberá ejecutarse directamente dentro del assert. Su resultado deberá almacenarse en una variable con un nombre descriptivo.

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

### 14.4 Un assert por test

Cada prueba deberá contener un solo assert. Esta es una política del equipo que busca que cada método verifique un único comportamiento y permita identificar con precisión la causa de un fallo. NUnit recomienda intentar mantener un assert por prueba, aunque el framework también admite la agrupación de varias comprobaciones (NUnit Project, s. f.-b).

Una verificación de NSubstitute mediante `Received()` o de Moq mediante `Verify()` contará como el único assert de la prueba.

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

Si una operación produce varios resultados que deben comprobarse por separado, se escribirá una prueba para cada comportamiento.

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

Cuando se espere una excepción, `Assert.Throws<TException>()` será el único assert de la prueba.

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

_verificar esto_
**Prohibición de `Assert.Multiple` y `Assert.EnterMultipleScope`**

No se utilizarán `Assert.Multiple` ni `Assert.EnterMultipleScope` en las pruebas unitarias del proyecto, ya que permiten agrupar varios asserts dentro de una sola prueba y contradicen la política del equipo de verificar un comportamiento por método. Esta prohibición es una decisión del equipo y no una limitación de NUnit.

**Con estándar**

```csharp
[Test]
public void Test_LevelUp_ExperienceReachesLimit_IncreasesLevel()
{
    Player player = new PlayerBuilder()
        .WithLevel(InitialLevel)
        .WithExperience(ExperienceBeforeLevelUp)
        .Build();

    player.AddExperience(EarnedExperience);

    Assert.That(player.Level, Is.EqualTo(ExpectedLevel));
}
```

**Sin estándar**

```csharp
[Test]
public void Test_LevelUp_ExperienceReachesLimit_UpdatesPlayer()
{
    Player player = new PlayerBuilder()
        .WithLevel(InitialLevel)
        .WithExperience(ExperienceBeforeLevelUp)
        .Build();

    player.AddExperience(EarnedExperience);

    Assert.Multiple(() =>
    {
        Assert.That(player.Level, Is.EqualTo(ExpectedLevel));
        Assert.That(player.Experience, Is.EqualTo(ExpectedExperience));
    });
}
```

### 14.5 Mocking de dependencias (interfaces + NSubstitute/Moq)

Los mocks deberán utilizarse únicamente para reemplazar dependencias externas o colaboradores cuyo comportamiento necesite controlarse durante una prueba.

El código de producción deberá depender de interfaces recibidas mediante el constructor. No deberá crear internamente implementaciones concretas de sus dependencias.

El equipo deberá seleccionar NSubstitute o Moq y utilizar una sola biblioteca en todo el proyecto. Los ejemplos siguientes muestran ambas alternativas, pero no deberán mezclarse dentro de la misma base de pruebas.

NSubstitute permite configurar resultados mediante `Returns()` y verificar llamadas mediante `Received()`. Moq proporciona las operaciones equivalentes mediante `Setup()` y `Verify()` (Devlooped, 2024; NSubstitute, s. f.).

**Dependencias mediante interfaces**

Las dependencias sustituibles deberán representarse mediante interfaces y recibirse mediante el constructor.

**Con estándar**

```csharp
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

**Selección de una biblioteca de mocking**

El proyecto deberá utilizar NSubstitute o Moq. No deberán incluirse ambas bibliotecas dentro del mismo proyecto de pruebas.

**Con estándar**

```csharp
using NSubstitute;
using NUnit.Framework;
```

**Sin estándar**

```csharp
using Moq;
using NSubstitute;
using NUnit.Framework;
```

**Configuración mediante NSubstitute**

Cuando el proyecto utilice NSubstitute, las dependencias deberán crearse mediante `Substitute.For<T>()` y configurarse mediante `Returns()`.

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

Cuando se compruebe una interacción, `Received()` será la única verificación de la prueba.

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

**Configuración mediante Moq**

Cuando el proyecto utilice Moq, las dependencias deberán crearse mediante `Mock<T>` y configurarse mediante `Setup()`.

**Con estándar**

```csharp
[Test]
public void Test_LoadPlayer_SaveExists_ReturnsStoredPlayer()
{
    Mock<ISaveGameRepository> saveGameRepositoryMock =
        new Mock<ISaveGameRepository>();
    Player expectedPlayer = new PlayerBuilder().Build();
    saveGameRepositoryMock
        .Setup(repository => repository.Load(PlayerSlot))
        .Returns(expectedPlayer);
    LoadGameService loadGameService =
        new LoadGameService(saveGameRepositoryMock.Object);

    Player actualPlayer = loadGameService.LoadPlayer(PlayerSlot);

    Assert.That(actualPlayer, Is.SameAs(expectedPlayer));
}
```

**Sin estándar**

```csharp
[Test]
public void Test_LoadPlayer_SaveExists_ReturnsStoredPlayer()
{
    Mock<FileSaveGameRepository> saveGameRepositoryMock =
        new Mock<FileSaveGameRepository>();
    LoadGameService loadGameService =
        new LoadGameService(saveGameRepositoryMock.Object);

    Player actualPlayer = loadGameService.LoadPlayer(PlayerSlot);

    Assert.That(actualPlayer, Is.Not.Null);
}
```

**Verificación mediante Moq**

Cuando se compruebe una interacción mediante Moq, `Verify()` será la única verificación de la prueba.

**Con estándar**

```csharp
[Test]
public void Test_GrantReward_RewardIsNotNull_AddsItemToInventory()
{
    Mock<IInventory> inventoryMock = new Mock<IInventory>();
    Item reward = new ItemBuilder().Build();
    RewardService rewardService =
        new RewardService(inventoryMock.Object);

    rewardService.GrantReward(reward);

    inventoryMock.Verify(
        inventory => inventory.Add(reward),
        Times.Once);
}
```

**Sin estándar**

```csharp
[Test]
public void Test_GrantReward_RewardIsNotNull_AddsItemToInventory()
{
    Mock<IInventory> inventoryMock = new Mock<IInventory>();
    Item reward = new ItemBuilder().Build();
    RewardService rewardService =
        new RewardService(inventoryMock.Object);

    rewardService.GrantReward(reward);

    inventoryMock.Verify(
        inventory => inventory.Add(It.IsAny<Item>()));
    inventoryMock.Verify(
        inventory => inventory.Add(reward));
}
```

**Objetos que no deben sustituirse**

No se crearán mocks de entidades, objetos de valor ni de la clase que se está probando. Estos objetos deberán construirse directamente o mediante builders.

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

### 14.6 Métodos builder para objetos de prueba complejos

Los builders de prueba se utilizarán para crear objetos complejos con valores válidos por defecto. Su propósito será reducir la repetición y permitir que cada prueba sobrescriba únicamente los valores relevantes para el escenario evaluado.

Los builders se almacenarán dentro de `tests/AdventureGame.Tests.Unit/Builders`. Su nombre deberá terminar con el sufijo `Builder`.

**Uso de builders para objetos complejos**

Se utilizará un builder cuando la creación directa de un objeto necesite varios parámetros o configuraciones.

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

La clase deberá utilizar el nombre del objeto construido y el sufijo `Builder`. Los métodos de configuración deberán utilizar el prefijo `With` y escribirse en `PascalCase`.

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

Un builder deberá producir un objeto válido aunque no se invoque ningún método `With`. Los valores predeterminados deberán representar el caso más común y neutral.

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

Cada método `With` deberá modificar una sola característica del objeto. No se utilizará un método para configurar varias propiedades sin relación directa.

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

Los métodos `With` deberán devolver la instancia actual mediante `return this;` para permitir el encadenamiento de llamadas.

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

El método `Build()` deberá devolver una nueva instancia en cada llamada. No deberá reutilizar un objeto mutable construido anteriormente.

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

Los builders no deberán contener asserts ni reglas de prueba. Su única responsabilidad será construir objetos.

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

Cada prueba deberá modificar únicamente las propiedades necesarias para representar su escenario.

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

### 15.2 Vulnerabilidades conocidas (formato CVE, aplica/no aplica)

<div style="page-break-after: always;"></div>

## 16. Referencias

- Cwalina, K., Barton, J., & Abrams, B. (2020). *Framework design guidelines: Conventions, idioms, and patterns for reusable .NET libraries* (3.ª ed.). Addison-Wesley Professional. [https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780135896372](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780135896372)

- Devlooped. (2024, 4 de julio). *Quickstart*. GitHub. [https://github.com/devlooped/moq/wiki/Quickstart](https://github.com/devlooped/moq/wiki/Quickstart)

- Microsoft. (2023, 3 de octubre). *Names of type members*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members)

- Microsoft. (2024, 27 de septiembre). *C# compiler options for language feature rules*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/compiler-options/language](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/compiler-options/language)

- Microsoft. (2025a, 22 de octubre). *Best practices for exceptions*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions](https://learn.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions)

- Microsoft. (2025b, 22 de marzo). *Best practices for writing unit tests*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices)

- Microsoft. (2025c, 30 de enero). *C# formatting options*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options)

- Microsoft. (2025d, 18 de enero). *Common C# code conventions*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)

- Microsoft. (2025e, 29 de mayo). *Names of classes, structs, and interfaces*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces)

- Microsoft. (2026a, 2 de abril). *CA1031: Do not catch general exception types*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/quality-rules/ca1031](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/quality-rules/ca1031)

- Microsoft. (2026b, 14 de julio). *C# identifier naming rules and conventions*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names)

- Microsoft. (2026c, 20 de enero). *Selection statements: `if`, `if-else`, and `switch`*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements)

- Microsoft. (2026d, 24 de marzo). *`switch` expression: Pattern matching expressions using the `switch` keyword*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression)

- Microsoft. (2026e, 20 de enero). *XML API documentation comments*. Microsoft Learn. [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/)

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
