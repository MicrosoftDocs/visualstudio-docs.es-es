---
title: Buscar pérdidas de memoria con la biblioteca CRT | Microsoft Docs
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
ms.openlocfilehash: e7fdfedbb2f632bdb0fcaa05c7f0fb282a8fcd2b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706033"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Búsqueda de fugas de memoria con la biblioteca de CRT

Pérdidas de memoria se encuentran entre los errores más sutiles y difíciles de detectar en las aplicaciones de C o C++. Resultado de error al desasignar correctamente memoria asignada previamente de pérdidas de memoria. Una pequeña pérdida de memoria podría no distinguirse en primer lugar, pero con el tiempo puede causar síntomas que van desde un bajo rendimiento hasta el bloqueo cuando se ejecuta la aplicación no hay memoria suficiente. Una aplicación de pérdidas que toda la memoria disponible puede dar lugar a otras aplicaciones que se bloquee, creando confusión con respecto a qué aplicación es responsable. Pérdidas de memoria aparentemente inocuas incluso podrían indicar otros problemas que se deben corregir.

 El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depurador y la biblioteca de tiempo de ejecución de C (CRT) pueden ayudarle a detectar e identificar las pérdidas de memoria.

## <a name="enable-memory-leak-detection"></a>Habilitar la detección de pérdidas de memoria

Funciones del montón de depuración de las herramientas principales para detectar pérdidas de memoria son el depurador de C o C++ y la biblioteca de tiempo de ejecución de C (CRT).

Para habilitar todas las funciones del montón de depuración, incluya las siguientes instrucciones en el programa de C++, en el orden siguiente:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

La instrucción `#define` asigna una versión base de las funciones del montón de CRT a la versión de depuración correspondiente. Si deja fuera la `#define` instrucción, el volcado de pérdida de memoria será [menos detallados](#interpret-the-memory-leak-report).

Incluyendo *crtdbg.h* asigna el `malloc` y `free` funciones a sus versiones de depuración [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) y [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), que realizan un seguimiento de memoria asignación y desasignación. Esta asignación se produce únicamente en las compilaciones de depuración, que tienen `_DEBUG`. Las versiones de lanzamiento utilizan las funciones normales `malloc` y `free` .

Después de habilitar las funciones del montón de depuración mediante el uso de las instrucciones anteriores, coloque una llamada a [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) antes de un punto de salida de la aplicación para mostrar un informe de pérdida de memoria cuando se cierra la aplicación.

```cpp
_CrtDumpMemoryLeaks();
```

Si la aplicación tiene varias salidas, no es necesario realizar manualmente `_CrtDumpMemoryLeaks` en cada punto de salida. Para hacer que una llamada automática a `_CrtDumpMemoryLeaks` en cada punto de salida, coloque una llamada a `_CrtSetDbgFlag` al principio de la aplicación con los campos de bits que se muestra aquí:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

De forma predeterminada, `_CrtDumpMemoryLeaks` genera el informe de pérdida de memoria en el panel de **Depuración** de la **Ventana de salida** . Si utiliza una biblioteca, esta podría hacer que se envíen los resultados a otra ubicación.

Puede usar `_CrtSetReportMode` redirigir el informe a otra ubicación, o espera a la **salida** ventana tal y como se muestra aquí:

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interpretación del informe de pérdida de memoria

Si la aplicación no define `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) muestra un informe de pérdida de memoria similar al siguiente:

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Si la aplicación define `_CRTDBG_MAP_ALLOC`, el informe de pérdida de memoria es similar a:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

El segundo informe muestra al nombre de archivo y número de línea donde primero se asigna la memoria perdida.

Si se define `_CRTDBG_MAP_ALLOC`, muestra el informe de pérdida de memoria:

- El número de asignación de memoria, que es `18` en el ejemplo
- El tipo de bloque, `normal` en el ejemplo.
- La ubicación de memoria hexadecimal, `0x00780E80` en el ejemplo.
- El tamaño del bloque, `64 bytes` en el ejemplo.
- Los primeros 16 bytes de datos del bloque, en formato hexadecimal.

Tipos de bloques de memoria son *normal*, *cliente*, o *CRT*. Un *bloque normal* se compone de memoria ordinaria asignada por el programa. Un *bloque cliente* es un tipo de bloque de memoria especial utilizado por programas MFC para objetos que requieren un destructor. El operador `new` de MFC crea un bloque normal o un bloque cliente, según convenga, para el objeto que se está creando.

Un *bloque CRT* es asignado por la biblioteca CRT para su propio uso. La biblioteca CRT controla la desasignación de estos bloques, por lo que los bloques CRT no aparecerán en el informe de pérdida de memoria a menos que haya problemas graves con la biblioteca CRT.

Hay otros dos tipos de bloques de memoria que no aparecen nunca en los informes de pérdida de memoria. Un *bloque libre* es memoria que se ha liberado, por lo que no se filtren por definición. Un *bloque omitido* es memoria que ha marcado explícitamente para excluirla del informe de pérdida de memoria.

Las técnicas anteriores identifican pérdidas de memoria para la memoria asignada con CRT estándar `malloc` función. Si el programa asigna memoria mediante C++ `new` operador, sin embargo, es posible que solo verá el nombre de archivo y número de línea donde `operator new` llamadas `_malloc_dbg` en el informe de pérdida de memoria. Para crear un informe de pérdida de memoria más útil, puede escribir una macro similar al siguiente para informar de la línea que realizó la asignación:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Ahora puede reemplazar el `new` operador mediante el uso de la `DBG_NEW` macro en el código. En las compilaciones de depuración, `DBG_NEW` usa una sobrecarga de global `operator new` que toma parámetros adicionales para el tipo de bloque, el archivo y el número de línea. La sobrecarga de `new` llamadas `_malloc_dbg` para registrar la información adicional. Los informes de pérdida de memoria muestran al nombre de archivo y número de línea donde se asignaron los objetos perdidos. Compilaciones de versión siguen usando el valor predeterminado `new`. Este es un ejemplo de la técnica:

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

Cuando se ejecuta este código en Visual Studio del depurador, la llamada a `_CrtDumpMemoryLeaks` genera un informe en el **salida** ventana similar a:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Este resultado de los informes que la asignación perdida estaba en la línea 20 del *debug_new.cpp*.

>[!NOTE]
>No se recomienda crear una macro de preprocesador denominada `new`, o cualquier otra palabra clave del lenguaje.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Establecer puntos de interrupción en un número de asignación de memoria

El número de asignación de memoria le indica cuándo se asignó un bloque de pérdida de memoria. Un bloque con un número de asignación de memoria de 18 años, por ejemplo, es el 18 de bloque de memoria asignado durante la ejecución de la aplicación. El informe de CRT cuenta todas las asignaciones de bloques de memoria durante la ejecución, incluidas las asignaciones por la biblioteca CRT y otras bibliotecas como MFC. Por lo tanto, el bloque número 18 de asignación de memoria probablemente no es el 18 de bloque de memoria asignado por el código.

Puede utilizar el número de asignación para establecer un punto de interrupción en la asignación de memoria.

**Para definir un punto de interrupción de asignación de memoria mediante la ventana Inspección:**

1. Establezca un punto de interrupción al principio de la aplicación e iniciar la depuración.

1. Cuando la aplicación se detiene en el punto de interrupción, abra un **inspección** ventana seleccionando **depurar** > **Windows** > **Inspección 1** (o **inspección 2**, **inspección 3**, o **inspección 4**).

1. En el **inspección** ventana, escriba `_crtBreakAlloc` en el **nombre** columna.

   Si usa la versión de DLL multiproceso de la biblioteca CRT (la opción /MD), agregue el operador de contexto: `{,,ucrtbased.dll}_crtBreakAlloc`

1. Presione **ENTRAR**.

   El depurador evalúa la llamada y coloca el resultado en la columna **Valor** . Este valor será **–1** si no se han definido puntos de interrupción sobre asignaciones de memoria.

1. En el **valor** columna, reemplace el valor con el número de asignación de la asignación de memoria donde desea que el depurador se interrumpa.

Después de establecer un punto de interrupción en un número de asignación de memoria, continuar la depuración. Asegúrese de que se ejecuten en las mismas condiciones, por lo que no cambia el número de asignación de memoria. Cuando el programa se interrumpe en la asignación de memoria especificada, use el **pila de llamadas** ventana y otras ventanas del depurador para determinar las condiciones en las que se asignó la memoria. A continuación, puede continuar la ejecución para observar lo que sucede en el objeto y determinar por qué no se desasigna correctamente.

También podría resultar útil definir un punto de interrupción de datos sobre el objeto. Para más información, vea [Uso de puntos de interrupción](../debugger/using-breakpoints.md).

También puede establecer puntos de interrupción de asignación de memoria en el código. Puede establecer:

```cpp
_crtBreakAlloc = 18;
```

 O bien

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Comparar los Estados de memoria
 Otra técnica para localizar pérdidas de memoria requiere tomar instantáneas del estado de la memoria de la aplicación en determinados puntos clave. Para tomar una instantánea del estado de memoria en un momento dado en la aplicación, cree un `_CrtMemState` estructurar y pasarlo a la `_CrtMemCheckpoint` función.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

El `_CrtMemCheckpoint` función rellena la estructura con una instantánea del estado actual de memoria.

Para generar el contenido de un `_CrtMemState` estructura, pase la estructura a la `_ CrtMemDumpStatistics` función:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` genera un volcado de memoria del estado similar al siguiente:

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

`_CrtMemDifference` Compara los Estados de memoria `s1` y `s2` y devuelve un resultado en (`s3`) que es la diferencia entre `s1` y `s2`.

Una técnica para buscar pérdidas de memoria empieza realizando `_CrtMemCheckpoint` llamadas al principio y al final de la aplicación, a continuación, usar `_CrtMemDifference` para comparar los resultados. Si `_CrtMemDifference` muestra una pérdida de memoria, puede agregar más `_CrtMemCheckpoint` llamadas para dividir el programa mediante una búsqueda binaria, hasta que se ha aislado el origen de la pérdida.

## <a name="false-positives"></a>Falsos positivos
 `_CrtDumpMemoryLeaks` puede proporcionar indicaciones falsas de pérdidas de memoria si una biblioteca que marca las asignaciones internas como bloques de tipo normal en lugar de los bloques CRT o bloques cliente. En tal caso, `_CrtDumpMemoryLeaks` no puede distinguir entre las asignaciones del usuario y las asignaciones de la biblioteca internas. Si los destructores globales de las asignaciones de biblioteca se ejecutan después del punto donde se llamó a `_CrtDumpMemoryLeaks`, cada asignación interna de la biblioteca se notifica como pérdida de memoria. Las versiones de la biblioteca de plantillas estándar anteriores a Visual Studio .NET puede causar `_CrtDumpMemoryLeaks` para informar de estos falsos positivos.

## <a name="see-also"></a>Vea también
- [Detalles del montón de depuración de CRT](../debugger/crt-debug-heap-details.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
