---
title: Buscar pérdidas de memoria con la biblioteca de CRT | Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb2729dcaf0da41c0adac24b0e1909a6d2697eb6
ms.sourcegitcommit: 697f2ab875fd789685811687387e9e8e471a38c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74829946"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Búsqueda de fugas de memoria con la biblioteca de CRT

Las fugas de memoria se encuentran entre los errores más sutiles y difíciles de detectar enC++ C/apps. Las pérdidas de memoria son consecuencia de un error al desasignar correctamente la memoria que se asignó previamente. Es posible que no se detecte una pequeña pérdida de memoria al principio, pero con el tiempo puede provocar síntomas que van desde un rendimiento deficiente hasta el bloqueo cuando la aplicación se queda sin memoria. Una aplicación con pérdida de memoria que utilice toda la memoria disponible puede hacer que se bloqueen otras aplicaciones y crear confusión en cuanto a qué aplicación es responsable. Incluso las pérdidas de memoria inocuas podrían indicar otros problemas que se deben corregir.

 El depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y la biblioteca en tiempo de ejecución de C (CRT) pueden ayudarle a detectar e identificar las pérdidas de memoria.

## <a name="enable-memory-leak-detection"></a>Habilitar la detección de pérdidas de memoria

Las herramientas principales para detectar pérdidas de memoria son las funciones del montónC++ de depuración de c/Debugger y de la biblioteca en tiempo de ejecución de c (CRT).

Para habilitar todas las funciones del montón de depuración, incluya las C++ siguientes instrucciones en el programa, en el orden siguiente:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

La instrucción `#define` asigna una versión base de las funciones del montón de CRT a la versión de depuración correspondiente. Si omite la instrucción `#define`, el volcado de pérdida de memoria será [menos detallado](#interpret-the-memory-leak-report).

Si se incluye *CRTDBG. h* , se asignan las funciones `malloc` y `free` a sus versiones de depuración, [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) y [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), que realizan el seguimiento de la asignación y desasignación de memoria. Esta asignación se produce únicamente en las compilaciones de depuración, que tienen `_DEBUG`. Las versiones de lanzamiento utilizan las funciones normales `malloc` y `free` .

Después de habilitar las funciones del montón de depuración mediante las instrucciones anteriores, coloque una llamada a [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) antes de un punto de salida de la aplicación para mostrar un informe de pérdida de memoria cuando se cierre la aplicación.

```cpp
_CrtDumpMemoryLeaks();
```

Si la aplicación tiene varias salidas, no es necesario colocar `_CrtDumpMemoryLeaks` manualmente en cada punto de salida. Para que se produzca una llamada automática a `_CrtDumpMemoryLeaks` en cada punto de salida, realice una llamada a `_CrtSetDbgFlag` al principio de la aplicación con los campos de bits que se muestran aquí:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

De forma predeterminada, `_CrtDumpMemoryLeaks` genera el informe de pérdida de memoria en el panel de **Depuración** de la **Ventana de salida** . Si utiliza una biblioteca, esta podría hacer que se envíen los resultados a otra ubicación.

Puede usar `_CrtSetReportMode` para redirigir el informe a otra ubicación o volver a la ventana de **salida** , como se muestra aquí:

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interpretar el informe de pérdida de memoria

Si la aplicación no define `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) muestra un informe de pérdida de memoria que tiene el siguiente aspecto:

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Si la aplicación define `_CRTDBG_MAP_ALLOC`, el informe de pérdida de memoria tiene el siguiente aspecto:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

El segundo informe muestra el nombre de archivo y el número de línea donde se asigna por primera vez la memoria perdida.

Tanto si define `_CRTDBG_MAP_ALLOC`como si no, el informe de pérdida de memoria muestra:

- El número de asignación de memoria, que se `18` en el ejemplo
- El tipo de bloque, `normal` en el ejemplo.
- La ubicación de memoria hexadecimal, `0x00780E80` en el ejemplo.
- Tamaño del bloque, `64 bytes` en el ejemplo.
- Los primeros 16 bytes de datos del bloque, en formato hexadecimal.

Los tipos de bloques de memoria son *normal*, *cliente*o *CRT*. Un *bloque normal* se compone de memoria ordinaria asignada por el programa. Un *bloque cliente* es un tipo de bloque de memoria especial utilizado por programas MFC para objetos que requieren un destructor. El operador `new` de MFC crea un bloque normal o un bloque cliente, según convenga, para el objeto que se está creando.

Un *bloque CRT* es asignado por la biblioteca CRT para su propio uso. La biblioteca CRT controla la desasignación de estos bloques, por lo que los bloques de CRT no aparecerán en el informe de pérdida de memoria, a menos que haya problemas graves con la biblioteca de CRT.

Hay otros dos tipos de bloques de memoria que no aparecen nunca en los informes de pérdida de memoria. Un *bloque libre* es la memoria que se ha liberado, por lo que, por definición, no se pierde. Un *bloque ignore* es una memoria que se ha marcado explícitamente para excluir del informe de pérdida de memoria.

Las técnicas anteriores identifican pérdidas de memoria para la memoria asignada mediante la función `malloc` de CRT estándar. Sin embargo, si el programa asigna memoria mediante C++ el operador `new`, es posible que solo vea el nombre de archivo y el número de línea donde `operator new` llama `_malloc_dbg` en el informe de pérdida de memoria. Para crear un informe de pérdida de memoria más útil, puede escribir una macro como la siguiente para informar de la línea que realizó la asignación:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Ahora puede reemplazar el operador `new` mediante el uso de la macro `DBG_NEW` en el código. En las compilaciones de depuración, `DBG_NEW` usa una sobrecarga de `operator new` global que toma parámetros adicionales para el tipo de bloque, el archivo y el número de línea. La sobrecarga de `new` llama a `_malloc_dbg` para registrar la información adicional. Los informes de pérdida de memoria muestran el nombre de archivo y el número de línea donde se asignaron los objetos perdidos. Las compilaciones de versión siguen usando el `new`predeterminado. A continuación se muestra un ejemplo de la técnica:

```cpp
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```

Al ejecutar este código en el depurador de Visual Studio, la llamada a `_CrtDumpMemoryLeaks` genera un informe en la ventana de **salida** que tiene un aspecto similar al siguiente:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Esta salida informa de que la asignación filtrada se encontraba en la línea 20 de *DEBUG_NEW. cpp*.

>[!NOTE]
>No se recomienda crear una macro de preprocesador denominada `new`o cualquier otra palabra clave de lenguaje.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Establecer puntos de interrupción en un número de asignación de memoria

El número de asignación de memoria le indica cuándo se asignó un bloque de pérdida de memoria. Un bloque con un número de asignación de memoria de 18, por ejemplo, es el decimoctavo bloque de memoria asignado durante la ejecución de la aplicación. El informe de CRT cuenta todas las asignaciones de bloques de memoria durante la ejecución, incluidas las asignaciones de la biblioteca CRT y otras bibliotecas como MFC. Por lo tanto, el bloque de asignación de memoria número 18 probablemente no es el 18 bloque de memoria asignado por el código.

Puede utilizar el número de asignación para establecer un punto de interrupción en la asignación de memoria.

**Para definir un punto de interrupción de asignación de memoria mediante la ventana Inspección:**

1. Establezca un punto de interrupción cerca del inicio de la aplicación e inicie la depuración.

1. Cuando la aplicación se detiene en el punto de interrupción, abra una ventana **inspección** seleccionando **depurar** > **Windows** > **Watch 1** (o **inspección 2**, **inspección 3**o **inspección 4**).

1. En la ventana **inspección** , escriba `_crtBreakAlloc` en la columna **nombre** .

   Si está utilizando la versión de DLL Multiproceso de la biblioteca CRT (la opción/MD), agregue el operador de contexto: `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Asegúrese de que se cargan los símbolos de depuración. De lo contrario `_crtBreakAlloc` se informará como no *identificado*.

1. Presione **ENTRAR**.

   El depurador evalúa la llamada y coloca el resultado en la columna **Valor** . Este valor será **–1** si no se han definido puntos de interrupción sobre asignaciones de memoria.

1. En la columna **valor** , reemplace el valor por el número de asignación de la asignación de memoria donde desea que se interrumpa el depurador.

Después de establecer un punto de interrupción en un número de asignación de memoria, continúe con la depuración. Asegúrese de ejecutarse en las mismas condiciones, por lo que no cambia el número de asignación de memoria. Cuando el programa se interrumpa en la asignación de memoria especificada, utilice la ventana **pila de llamadas** y otras ventanas del depurador para determinar las condiciones en las que se asignó la memoria. Después, puede continuar con la ejecución para observar lo que ocurre en el objeto y determinar por qué no se ha desasignado correctamente.

También podría resultar útil definir un punto de interrupción de datos sobre el objeto. Para más información, vea [Uso de puntos de interrupción](../debugger/using-breakpoints.md).

También puede establecer puntos de interrupción de asignación de memoria en el código. Puede establecer:

```cpp
_crtBreakAlloc = 18;
```

 o bien:

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Comparar Estados de memoria
 Otra técnica para localizar pérdidas de memoria requiere tomar instantáneas del estado de la memoria de la aplicación en determinados puntos clave. Para tomar una instantánea del estado de la memoria en un punto determinado de la aplicación, cree una estructura de `_CrtMemState` y pásela a la función `_CrtMemCheckpoint`.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

La función `_CrtMemCheckpoint` rellena la estructura con una instantánea del estado actual de la memoria.

Para generar el contenido de una estructura de `_CrtMemState`, pase la estructura a la función `_ CrtMemDumpStatistics`:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` genera un volcado del estado de la memoria que tiene el siguiente aspecto:

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

Para determinar si se ha producido una pérdida de memoria en una sección de código, puede tomar instantáneas del estado de la memoria antes y después de la sección y, a continuación, utilizar `_ CrtMemDifference` para comparar los dos estados:

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference` compara los Estados de memoria `s1` y `s2` y devuelve un resultado en (`s3`) que es la diferencia entre `s1` y `s2`.

Una técnica para buscar pérdidas de memoria comienza colocando `_CrtMemCheckpoint` llamadas al principio y al final de la aplicación y usando `_CrtMemDifference` para comparar los resultados. Si `_CrtMemDifference` muestra una pérdida de memoria, puede agregar más `_CrtMemCheckpoint` llamadas para dividir el programa mediante una búsqueda binaria hasta que haya aislado el origen de la pérdida.

## <a name="false-positives"></a>Falsos positivos
 `_CrtDumpMemoryLeaks` puede proporcionar indicaciones falsas de pérdidas de memoria si una biblioteca marca las asignaciones internas como bloques normales en lugar de bloques de CRT o bloques de cliente. En tal caso, `_CrtDumpMemoryLeaks` no puede distinguir entre las asignaciones del usuario y las asignaciones de la biblioteca internas. Si los destructores globales de las asignaciones de biblioteca se ejecutan después del punto donde se llamó a `_CrtDumpMemoryLeaks`, cada asignación interna de la biblioteca se notifica como pérdida de memoria. Las versiones de la biblioteca de plantillas estándar anteriores a Visual Studio .NET pueden hacer que `_CrtDumpMemoryLeaks` informe de estos falsos positivos.

## <a name="see-also"></a>Vea también
- [Detalles del montón de depuración de CRT](../debugger/crt-debug-heap-details.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
