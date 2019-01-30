---
title: Advertencias y errores | Herramientas de prueba para desarrolladores de Microsoft IntelliTest
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e6c58aa23e4b5c3133de2bee8f29b3205cf7aff9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942637"
---
# <a name="warnings-and-errors"></a>Advertencias y errores

## <a name="warnings-and-errors-by-category"></a>Advertencias y errores por categoría

* **Límites**
  * [MaxBranches superado](#maxbranches-exceeded)
  * [MaxConstraintSolverTime superado](#maxconstraintsolvertime-exceeded)
  * [MaxConditions superado](#maxconditions-exceeded)
  * [MaxCalls superado](#maxcalls-exceeded)
  * [MaxStack superado](#maxstack-exceeded)
  * [MaxRuns superado](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests superado](#maxrunswithoutnewtests-exceeded)<p />

* **Solución de restricciones**
  * [No se puede concretizar la solución](#cannot-concretize-solution)<p />

* **Dominios**
  * [Se necesita ayuda para construir el objeto](#help-construct)
  * [Se necesita ayuda para buscar tipos](#help-types)
  * [Tipo utilizable estimado](#usable-type-guessed)<p />

* **Ejecución**
  * [Error inesperado durante la exploración](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)<p />

* **Instrumentación**
  * [Método no instrumentado llamado](#uninstrumented-method-called)
  * [Método externo llamado](#external-method-called)
  * [Método sin capacidad de instrumentación llamado](#uninstrumentable-method-called)
  * [Problema de capacidad de prueba](#testability-issue)
  * [Limitación](#limitation)<p />

* **Intérprete**
  * [Error de coincidencia de llamadas observado](#observed-call-mismatch)
  * [Se almacenó un valor en el campo estático](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches superado

IntelliTest limita la longitud de cualquier ruta de ejecución que explora durante la [generación de entradas](input-generation.md). Esta característica evita que IntelliTest deje de responder cuando el programa entra en un bucle infinito.

Cada rama condicional e incondicional del código supervisado y ejecutado se cuenta para calcular este límite, incluidas las ramas que no dependen de las entradas de la [prueba unitaria parametrizada](test-generation.md#parameterized-unit-testing).

Por ejemplo, el código siguiente consume ramas del orden de 100:

```csharp
for (int i=0; i<100; i++) { }
```

Puede editar la opción **MaxBranches** de un atributo derivado de **PexSettingsAttributeBase**, como [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). El ejemplo siguiente quita este límite de manera eficaz:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

También puede establecer la opción **TestExcludePathBoundsExceeded** para informar a IntelliTest de cómo tratar generalmente con estos problemas.

En el código de prueba, puede usar [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) para ignorar las restricciones que se han generado mediante la condición de bucle:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime superado

IntelliTest usa un [solucionador de restricciones](input-generation.md#constraint-solver) para calcular nuevas entradas de prueba. La solución de restricciones puede ser un proceso muy lento, por lo que IntelliTest le permite configurar límites; en concreto, **MaxConstraintSolverTime**.

Para muchas aplicaciones, aumentar significativamente el tiempo de espera no provocará una cobertura mejor. La razón de esto es que la mayoría de los tiempos de espera se provocan por sistemas de restricción que no tienen soluciones. En cambio, IntelliTest puede que no sea capaz de determinar que es incoherente sin intentar todas las soluciones posibles, lo que provoca tiempo de espera.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions superado

IntelliTest limita la longitud de cualquier ruta de ejecución que explora durante la [generación de entradas](input-generation.md). Esta característica evita que IntelliTest deje de responder cuando el programa entra en un bucle infinito.

Cada rama condicional que depende de las entradas de la [prueba unitaria parametrizada](test-generation.md#parameterized-unit-testing) se cuenta para calcular este límite.

Por ejemplo, cada ruta del siguiente código consume **n+1** condiciones:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++)
    { ... }
}
```

Puede editar la opción **MaxConditions** de un atributo derivado de **PexSettingsAttributeBase**, como [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). Por ejemplo:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

También puede establecer la opción **TestExcludePathBoundsExceeded** para informar a IntelliTest de cómo tratar generalmente con estos problemas.

Puede usar [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) para ignorar las restricciones que se han generado mediante la condición de bucle:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>MaxCalls superado

IntelliTest limita la longitud de cualquier ruta de ejecución que explora durante la [generación de entradas](input-generation.md). Esta característica evita que IntelliTest deje de responder cuando el programa entra en un bucle infinito.

Cada llamada (directa, indirecta, virtual o salto) del código supervisado y ejecutado se cuenta para calcular este límite.

Puede editar la opción **MaxCalls** de un atributo derivado de **PexSettingsAttributeBase**, como [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). El ejemplo siguiente quita este límite de manera eficaz:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

También puede establecer la opción **TestExcludePathBoundsExceeded** para informar a IntelliTest de cómo tratar generalmente con estos problemas.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack superado

IntelliTest limita el tamaño de la pila de llamadas de cualquier ruta de ejecución que explora durante la [generación de entradas](input-generation.md). Esta característica evita que IntelliTest finalice cuando se produce un desbordamiento de pila.

Puede editar la opción **MaxStack** de un atributo derivado de **PexSettingsAttributeBase**, como [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). El ejemplo siguiente quita este límite de manera eficaz (no recomendado):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

También puede establecer la opción **TestExcludePathBoundsExceeded** para informar a IntelliTest de cómo tratar generalmente con estos problemas.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns superado

IntelliTest limita el número de rutas de ejecución que explora durante la [generación de entradas](input-generation.md). Esta característica garantiza que IntelliTest finalice cuando el programa tenga bucles o recursividad.

Puede que no sea el caso de que cada vez que IntelliTest ejecuta la prueba parametrizada con entradas concretas, emita un nuevo caso de prueba. Vea [TestEmissionFilter](exploration-bounds.md#testemissionfilter) para obtener más información.

Puede editar la opción **MaxRuns** de un atributo derivado de **PexSettingsAttributeBase**, como [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). El ejemplo siguiente quita este límite de manera eficaz (no recomendado):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests superado

IntelliTest limita el número de rutas de ejecución que explora durante la [generación de entradas](input-generation.md). Esta característica garantiza que IntelliTest finalice cuando el programa tenga bucles o recursividad.

Puede que no sea el caso de que cada vez que IntelliTest ejecuta la prueba parametrizada con entradas concretas, emita un nuevo caso de prueba. Vea [TestEmissionFilter](exploration-bounds.md#testemissionfilter) para obtener más información.

Aunque a menudo IntelliTest encuentra muchas entradas de prueba interesantes al principio, puede que después de un tiempo no emita más pruebas. Esta opción controla durante cuánto tiempo IntelliTest puede seguir intentando buscar otra entrada de prueba relevante.

Puede editar la opción **MaxRunsWithoutNewTests** de un atributo derivado de **PexSettingsAttributeBase**, como [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). El ejemplo siguiente quita este límite de manera eficaz (no recomendado):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>No se puede concretizar la solución

A menudo este error es la consecuencia de un error anterior. IntelliTest usa un [solucionador de restricciones](input-generation.md#constraint-solver) para determinar nuevas entradas de prueba. A veces, las entradas de prueba propuestas por el [solucionador de restricciones](input-generation.md#constraint-solver) no son válidas. Esto puede suceder cuando:

* determinadas restricciones no se conocen;
* si los valores se han creado de una manera definida por el usuario, provocando errores que se producen en el código de usuario;
* algunos de los tipos implicados tienen una lógica de inicialización no controlada por IntelliTest (por ejemplo, clases COM).

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Se necesita ayuda para construir el objeto

IntelliTest [genera entradas de prueba](input-generation.md) y algunas de las entradas pueden ser objetos con campos.
Aquí, IntelliTest intenta generar una instancia de una clase que tiene un campo privado, y presupone que se producirá un comportamiento de un programa interesante cuando este campo privado tenga un valor determinado.

En cambio, aunque es posible con la reflexión, IntelliTest no produce objetos con valores de campo arbitrarios.
En su lugar, en estos casos, se basa en el usuario para proporcionar sugerencias sobre cómo usar los métodos públicos de una clase para crear un objeto, e incorporarlo en un estado donde su campo privado tenga el valor deseado.

Lea [Creación de instancias de las clases existentes](input-generation.md#existing-classes) para obtener información sobre cómo puede ayudar a IntelliTest a crear objetos interesantes.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Se necesita ayuda para buscar tipos

IntelliTest [genera entradas de prueba](input-generation.md) para cualquier tipo .NET. Aquí, IntelliTest intenta crear una instancia que derive de una clase abstracta o implemente una interfaz abstracta, e IntelliTest no conoce ningún tipo que cumpla las restricciones.

Puede ayudar a IntelliTest indicando uno o más tipos que coincidan con las restricciones. Normalmente, le ayudará uno de los siguientes atributos:

* **PexUseTypeAttribute**, que indica un tipo concreto.

  Por ejemplo, si IntelliTest notifica que "no conoce ningún tipo que se pueda asignar a **System.Collections.IDictionary**", puede ayudarle adjuntando el siguiente atributo **PexUseTypeAttribute** a la prueba (o a la clase de corrección):

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Un atributo de nivel de ensamblado**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Tipo utilizable estimado

IntelliTest [genera entradas de prueba](input-generation.md) para cualquier tipo .NET. Cuando un tipo es abstracto o una interfaz, IntelliTest debe elegir una implementación determinada de ese tipo. Para realizar esa elección, necesita conocer qué tipos existen.

Cuando se muestra esta advertencia, indica que IntelliTest ha examinado algunos ensamblados a los que se hace referencia y ha detectado un tipo de implementación, pero no está seguro de si debe usar ese tipo o de si existen tipos más apropiados disponibles en otro lugar. IntelliTest simplemente ha elegido un tipo que parecía prometedor.

Para evitar esta advertencia, puede aceptar la elección de tipo de IntelliTest o ayudar a IntelliTest a usar otros tipos agregando un elemento [PexUseType](attribute-glossary.md#pexusetype) correspondiente.

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Error inesperado durante la exploración

Se ha producido una excepción inesperada al explorar una prueba.

[Notifique esto como un error](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Se ha producido una excepción en el código de usuario. Inspeccione el seguimiento de la pila y quite el error en su código.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Método no instrumentado llamado

IntelliTest [genera entradas de prueba](input-generation.md) mediante la supervisión de la ejecución del programa. Es esencial que el código relevante se instrumentalice correctamente de manera que IntelliTest pueda supervisar su comportamiento.

Esta advertencia aparece cuando el código instrumentado llama a métodos en otro ensamblado no instrumentado.
Si quiere que IntelliTest explore la interacción de ambos, también debe instrumentar el otro ensamblado (o partes de este).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Método externo llamado

IntelliTest [genera entradas de prueba](input-generation.md) mediante la supervisión de la ejecución de aplicaciones .NET.
IntelliTest no puede generar entradas de prueba significativas para el código que no se ha escrito en un lenguaje .NET.

Esta advertencia aparece cuando el código instrumentado llama a un método nativo, no administrado que IntelliTest no puede analizar. Si quiere que IntelliTest explore la interacción de ambos, debe imitar el método no administrado.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Método sin capacidad de instrumentación llamado

IntelliTest [genera entradas de prueba](input-generation.md) mediante la supervisión de la ejecución de aplicaciones .NET. En cambio, existen algunos métodos que, por motivos técnicos, IntelliTest no puede supervisar. Por ejemplo, IntelliTest no puede supervisar un constructor estático.

Esta advertencia aparece cuando el código instrumentado llama a un método que IntelliTest no puede supervisar.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problema de capacidad de prueba

IntelliTest [genera entradas de prueba](input-generation.md) mediante la supervisión de la ejecución del programa. Solo puede generar entradas de prueba relevantes cuando el programa sea determinista, y cuando el comportamiento relevante esté controlado por entradas de prueba.

Esta advertencia aparece porque, durante la ejecución de su caso de prueba, se ha llamado a un método que se comporta de manera no determinista o que interactúa con el entorno. Los ejemplos son métodos de **System.Random** y **System.IO.File**. Si quiere que IntelliTest cree entradas de prueba significativas, debe imitar los métodos que IntelliTest marca como problemas de capacidad de prueba.

<a name="limitation"></a>
## <a name="limitation"></a>Limitación

IntelliTest [genera entradas de prueba](input-generation.md) mediante un [solucionador de restricciones](input-generation.md#constraint-solver).
En cambio, existen algunas operaciones que están más allá del ámbito del [solucionador de restricciones](input-generation.md#constraint-solver).
Esto actualmente incluye:

* la mayoría de las operaciones de punto flotante (solo se admite parte de aritmética lineal en los números de punto flotante)
* conversiones entre los números de punto flotante y los enteros
* todas las operaciones del tipo **System.Decimal**

Esta advertencia aparece cuando el código ejecutado realiza una operación o llama a un método que IntelliTest no puede interpretar.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Error de coincidencia de llamadas observado

IntelliTest [genera entradas de prueba](input-generation.md) mediante la supervisión de la ejecución del programa. En cambio, IntelliTest puede que no sea capaz de supervisar todas las instrucciones. Por ejemplo, no puede supervisar código nativo y no puede supervisar código que no esté instrumentado.

Cuando IntelliTest no puede supervisar código, no puede generar entradas de prueba que son relevantes para ese código.
A menudo, IntelliTest no es consciente del hecho de que no puede supervisar un método hasta que se devuelve una llamada a ese método. En cambio, la causa de esta advertencia es:

* IntelliTest ha supervisado código, que ha iniciado una llamada a un método no instrumentado
* El método no instrumentado ha llamado a un método que está instrumentado
* IntelliTest supervisa el método instrumentado al que se ha llamado

IntelliTest no conoce qué ha realizado el método intermedio no instrumentado, por lo que puede que no sea capaz de generar entradas de prueba que son relevantes para la llamada instrumentada anidada.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Se almacenó un valor en el campo estático

IntelliTest puede determinar sistemáticamente [entradas de prueba relevantes](input-generation.md) solo cuando la prueba unitaria es determinista; en otras palabras, siempre se comporta de la misma manera para las mismas entradas de prueba. En concreto, esto significa que la prueba debe dejar el sistema en un estado que permita volver a ejecutar esa prueba.
Idealmente, la prueba unitaria no debe cambiar ningún estado global, pero todas las interacciones con globales deben imitarse.

Esta advertencia indica que se ha cambiado un campo estático; esto puede hacer que la prueba se comporte de manera no determinista.

En algunas situaciones, es aceptable cambiar un campo estático:

* cuando las entradas de prueba hacen que el código de limpieza o instalación deshaga el cambio
* cuando el campo solo se inicia una vez, y el valor no cambia después

<a name="report-bug"></a>

## <a name="got-feedback"></a>¿Tiene comentarios?

Publique sus ideas y solicitudes de características en [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).