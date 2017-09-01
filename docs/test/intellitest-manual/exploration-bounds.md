---
title: "Límites de exploración | Herramientas de prueba para desarrolladores de Microsoft IntelliTest | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.assetid: 9E0751B3-CE7E-49D4-833E-F1C2709E57C1
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: e3b4ddd14bf150f17966f52862e2a4c392fd55ce
ms.contentlocale: es-es
ms.lasthandoff: 06/02/2017

---
# <a name="exploration-bounds"></a>Límites de exploración

**PexSettingsAttributeBase** es la clase base abstracta para establecer límites como atributos. Vea [Settings Waterfall](settings-waterfall.md) (Cascada de configuración) para obtener información general de la configuración de IntelliTest.

Puede modificar la configuración mediante propiedades con nombre de esta y sus atributos derivados:

```
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Límites de solución de restricciones**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime): el número de segundos que el [solucionador de restricciones](input-generation.md#constraint-solver) tiene para detectar entradas que provocarán una nueva y diferente ruta de ejecución que se va a seguir.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory): el tamaño en megabytes que puede usar el [solucionador de restricciones](input-generation.md#constraint-solver) para detectar entradas.<p />
* **Límites de la ruta de exploración**
  * [MaxBranches](#maxbranches): el número máximo de ramas que se pueden tomar a lo largo de una sola ruta de ejecución.
  * [MaxCalls](#maxcalls): el número máximo de llamadas que pueden realizarse durante una sola ruta de ejecución.
  * [MaxStack](#maxstack): el tamaño máximo de la pila en cualquier momento durante una sola ruta de ejecución, medido como el número de marcos de llamada activos.
  * [MaxConditions](#maxconditions): el número máximo de condiciones en las entradas que se pueden comprobar durante una sola ruta de acceso de ejecución.<p />
* **Límites de exploración**
  * [MaxRuns](#maxruns): el número máximo de ejecuciones que se intentarán durante una exploración.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests): el número máximo de ejecuciones consecutivas sin que se emita una nueva prueba.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths): el número máximo de ejecuciones con rutas de ejecución únicas que se intentarán durante una exploración.
  * [MaxExceptions](#maxexceptions): el número máximo de excepciones que pueden detectarse para una combinación de todas las rutas de ejecución detectadas.<p />
* **Configuración de la generación de código para el conjunto de pruebas**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded): cuando se establezca en True, las rutas de ejecución que exceden cualquiera de los límites de ruta ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)) se ignoran.
  * [TestEmissionFilter](#testemissionfilter): indica en qué circunstancias IntelliTest debe emitir pruebas.
  * [TestEmissionBranchHits](#testemissionbranchhits): controla cuántas pruebas emite IntelliTest.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

El número de segundos que el [solucionador de restricciones](input-generation.md#constraint-solver) tiene para calcular entradas que provocarán una nueva y diferente ruta de ejecución que se va a tomar. Esta es una opción de **PexSettingsAttributeBase** y de sus tipos derivados.

Cuanto mayor es la profundidad con la que IntelliTest explora las rutas de ejecución de un programa, más complejos se convierten los sistemas de restricciones que IntelliTest crea del flujo de control y el flujo de datos del programa. Dependiendo de la limitación temporal, puede establecer este valor para permitir que IntelliTest tarde más o menos tiempo en detectar nuevas rutas de ejecución.

Normalmente, la razón del tiempo de espera es que IntelliTest está intentando buscar una solución para un sistema de restricciones que no tiene solución, pero no es consciente de este hecho. Como este es el caso más común de tiempo de espera, puede que no tenga sentido aumentar el límite.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

El número de megabytes que el [solucionador de restricciones](input-generation.md#constraint-solver) tiene para calcular entradas que provocarán una nueva y diferente ruta de ejecución que se va a tomar. Esta es una opción de **PexSettingsAttributeBase** y de sus tipos derivados.

Cuanto mayor es la profundidad con la que IntelliTest explora las rutas de ejecución de un programa, más complejos se convierten los sistemas de restricciones que IntelliTest crea del flujo de control y el flujo de datos del programa. Dependiendo de la memoria disponible de su equipo, puede establecer este valor para permitir que IntelliTest trate sistemas de restricciones más complejos.

Normalmente, la razón del tiempo de espera es que IntelliTest está intentando buscar una solución para un sistema de restricciones que no tiene solución, pero no es consciente de este hecho. Como este es el caso más común de una situación de memoria insuficiente, puede que no tenga sentido aumentar el límite.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

El número máximo de ramas que se pueden tomar a lo largo de una sola ruta de ejecución.

La motivación para este límite de exploración es limitar la longitud de cualquier ruta de ejecución que IntelliTest explora durante la [generación de entradas](input-generation.md). En concreto, evita que IntelliTest deje de responder si el programa entra en un bucle infinito.

Cada rama condicional e incondicional del código supervisado y ejecutado se cuenta para calcular este límite, incluidas las ramas que no dependen de las entradas de la prueba parametrizada.

Por ejemplo, el código siguiente consume ramas del orden de 100:

```
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

El número máximo de llamadas que pueden realizarse durante una sola ruta de ejecución.

La motivación para este límite de exploración es limitar la longitud de cualquier ruta de ejecución que IntelliTest explora durante la [generación de entradas](input-generation.md). En concreto, evita que IntelliTest deje de responder si el programa llama a un método recursivamente un número infinito de veces, lo que provocaría un desbordamiento de pila del que IntelliTest no puede recuperarse.

Cada llamada (directa, indirecta, virtual, salto) del código supervisado y ejecutado se cuenta para calcular este límite.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

El tamaño máximo de la pila en cualquier momento durante una sola ruta de ejecución, medido por el número de marcos de llamada activos.

La motivación para este límite de exploración es limitar el tamaño de la pila de cualquier ruta de ejecución que IntelliTest explora durante la [generación de entradas](input-generation.md). En concreto, evita que IntelliTest use todo el espacio de la pila disponible, lo que provocaría un desbordamiento de pila del que IntelliTest no puede recuperarse.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

El número máximo de condiciones en las entradas que se pueden comprobar durante una sola ruta de acceso de ejecución.

La motivación para este límite de exploración es limitar la complejidad de cualquier ruta de ejecución que IntelliTest explora durante la [generación de entradas](input-generation.md). Cada rama condicional que depende de las entradas de la prueba parametrizada se cuenta para calcular este límite.

Por ejemplo, cada ruta del siguiente código consume n+1 condiciones:

```
[PexMethod]
void ParameterizedTest(int n) 
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

El número máximo de ejecuciones que IntelliTest probará durante la exploración de una prueba.

La motivación para este límite de exploración es que cualquier código que contiene bucles o recursividad pueda tener un número infinito de rutas de ejecución y, por lo tanto, IntelliTest necesita limitarse durante la [generación de entradas](input-generation.md). 

Las dos opciones **MaxRuns** y **MaxRunsWithUniquePaths** se relacionan de la manera siguiente: 

* IntelliTest llamará a un método de prueba parametrizado hasta **MaxRuns** veces con diferentes entradas de prueba.
* Si el código de prueba es determinista, IntelliTest tomará una ruta de ejecución diferente cada vez. 
  En cambio, en determinadas condiciones el código ejecutado puede seguir una ruta de ejecución que ya haya tomado antes, con entradas diferentes. 
* IntelliTest cuenta el número de rutas de ejecución únicas que detecta; este número está limitado mediante la opción **MaxRunsWithUniquePaths**.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

El número máximo de ejecuciones consecutivas sin que se emita una nueva prueba.

Aunque a menudo IntelliTest puede detectar muchas entradas de pruebas interesantes en un breve período, después de un tiempo no detectará ninguna entrada de prueba nueva y no emitirá más pruebas unitarias. Esta opción de configuración coloca un límite en el número de intentos consecutivos que IntelliTest puede realizar sin emitir una prueba nueva. Cuando se alcanza, detendrá la exploración. 

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

El número máximo de rutas únicas que IntelliTest considerará durante una exploración.

La motivación para este límite de exploración es que cualquier código que contiene bucles o recursividad pueda tener un número infinito de rutas de ejecución y, por lo tanto, IntelliTest debe limitarse durante la [generación de entradas](input-generation.md).

Las dos opciones **MaxRuns** y **MaxRunsWithUniquePaths** se relacionan de la manera siguiente: 

* IntelliTest llamará a un método de prueba parametrizado hasta **MaxRuns** veces con diferentes entradas de prueba.
* Si el código de prueba es determinista, IntelliTest tomará una ruta de ejecución diferente cada vez. 
  En cambio, en determinadas condiciones el código ejecutado puede seguir una ruta de ejecución que ya haya tomado antes, con entradas diferentes. 
* IntelliTest cuenta el número de rutas de ejecución únicas que detecta; este número está limitado mediante la opción **MaxRunsWithUniquePaths**.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

El número máximo de excepciones que pueden encontrarse antes de que se detenga la exploración.

La motivación para este límite de exploración es detener la exploración del código que contiene muchos errores.
Si IntelliTest detecta demasiados errores en el código, se detiene la exploración.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Las rutas de ejecución que exceden los límites de ruta que se han configurado [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack) y [MaxConditions](#maxconditions) se ignoran.

La motivación para este límite de exploración es tratar (muy probablemente) con pruebas de no terminación. Cuando IntelliTest alcanza un límite de exploración como [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack) o [MaxConditions](#maxconditions), presupone que la prueba no será un proceso de no terminación y que no provocará un desbordamiento de pila después.
Dichos casos de prueba pueden presentar problemas en otros marcos de prueba, y este atributo proporciona una manera de evitar que IntelliTest emita casos de prueba para los procesos de no terminación potenciales o los casos de prueba que provocarán un desbordamiento de pila.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Indica los tipos de pruebas que debe emitir IntelliTest. Los valores posibles son:

* **All**: emite pruebas para todo, incluidas las infracciones de hipótesis.
* **FailuresAndIncreasedBranchHits** (el valor predeterminado): emite pruebas para todos los errores únicos, y cada vez que un caso de prueba aumenta la cobertura que se controla mediante [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths**: emite pruebas para todos los errores que IntelliTest detecta, y también para cada entrada de prueba que provoca una ruta de ejecución única.
* **Failures**: emite pruebas solo para los errores.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

Dependiendo de la opción [TestEmissionFilter](#testemissionfilter) actual, IntelliTest emite nuevos casos de prueba cuando cubren una rama del programa que no se ha cubierto antes.

La opción **TestEmissionBranchHits** determina si IntelliTest solo debe considerar si una rama se ha cubierto por completo (**TestEmissionBranchHits=1**), si una prueba la ha cubierto una o dos veces (**TestEmissionBranchHits=2**), y así sucesivamente.

**TestEmissionBranchHits=1** producirá un conjunto de pruebas muy pequeño que cubrirá todas las ramas que IntelliTest puede alcanzar. En concreto, este conjunto de pruebas también cubrirá todos los bloques básicos y las instrucciones que ha alcanzado. 

El valor predeterminado de esta opción es **TestEmissionBranchHits=2**, que genera un conjunto de pruebas más expresivo que también es más adecuado para detectar futuros errores de regresiones.

## <a name="got-feedback"></a>¿Tiene comentarios?

Publique sus ideas y solicitudes de características en **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.

