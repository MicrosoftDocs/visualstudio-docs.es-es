---
title: Búsqueda de fugas de memoria con la biblioteca de CRT | Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 4ae879d8ed03653959ae926cc372300db9b71b9f
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182656"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Búsqueda de fugas de memoria con la biblioteca de CRT

Las fugas de memoria se encuentran entre los errores más sutiles y difíciles de detectar en aplicaciones C/C++. Las fugas de memoria son consecuencia de un error al desasignar correctamente la memoria que previamente se había asignado. Es posible que no se detecte una pequeña fuga de memoria al principio, pero con el tiempo puede provocar síntomas que van desde un rendimiento deficiente hasta el bloqueo cuando la aplicación se queda sin memoria. Una aplicación con fugas de memoria que utilice toda la memoria disponible puede provocar el bloqueo de otras aplicaciones y crear confusión respecto a qué aplicación es la responsable. Incluso unas fugas de memoria inocuas podrían indicar otros problemas que se deben corregir.

El depurador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y la biblioteca en tiempo de ejecución de C (CRT) pueden ayudarle a detectar e identificar las fugas de memoria.

## <a name="enable-memory-leak-detection"></a>Habilitación de la detección de fugas de memoria

Las herramientas principales para detectar fugas de memoria son el depurador de C/C++ y las funciones del montón de depuración de la biblioteca en tiempo de ejecución de C (CRT).

Para habilitar todas las funciones del montón de depuración, incluya las siguientes instrucciones en el programa de C++, en el orden siguiente:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

La instrucción `#define` asigna una versión base de las funciones del montón de CRT a la versión de depuración correspondiente. Si omite la instrucción `#define`, el volcado de fuga de memoria será [menos detallado](#interpret-the-memory-leak-report).

Si se incluye *crtdbg.h*, se asignan las funciones `malloc` y `free` a sus versiones de depuración [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) y [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), que realizan un seguimiento de la asignación y desasignación de memoria. Esta asignación se produce únicamente en las compilaciones de depuración, que tienen `_DEBUG`. Las versiones de lanzamiento utilizan las funciones normales `malloc` y `free` .

Después de habilitar las funciones del montón de depuración mediante las instrucciones anteriores, coloque una llamada a [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) antes de un punto de salida de la aplicación para mostrar un informe de fuga de memoria cuando se cierre la aplicación.

```cpp
_CrtDumpMemoryLeaks();
```

Si la aplicación tiene varias salidas, no es necesario colocar `_CrtDumpMemoryLeaks` manualmente en cada punto de salida. Para que se produzca una llamada automática a `_CrtDumpMemoryLeaks` en cada punto de salida, coloque una llamada a `_CrtSetDbgFlag` al principio de la aplicación con los campos de bits que se muestran aquí:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

De forma predeterminada, `_CrtDumpMemoryLeaks` genera el informe de pérdida de memoria en el panel de **Depuración** de la **Ventana de salida** . Si utiliza una biblioteca, esta podría hacer que se envíen los resultados a otra ubicación.

Puede usar `_CrtSetReportMode` para redirigir el informe a otra ubicación o volver a la ventana **Salida** como se muestra aquí:

```cpp
_CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interpretación del informe de fuga de memoria

Si la aplicación no define `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) muestra un informe de fuga de memoria con esta apariencia:

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Si la aplicación define `_CRTDBG_MAP_ALLOC`, el informe de fuga de memoria tiene el siguiente aspecto:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

El segundo informe muestra el nombre de archivo y el número de línea donde se asigna por primera vez la memoria perdida.

Tanto si define `_CRTDBG_MAP_ALLOC` como si no, el informe de fuga de memoria muestra lo siguiente:

- El número de asignación de memoria, que es `18` en este ejemplo.
- El tipo de bloque, `normal` en este ejemplo.
- La ubicación de memoria hexadecimal, `0x00780E80` en este ejemplo.
- El tamaño del bloque, `64 bytes` en este ejemplo.
- Los primeros 16 bytes de datos del bloque, en formato hexadecimal.

Los tipos de bloques de memoria son *normal*, *cliente* o *CRT*. Un *bloque normal* se compone de memoria ordinaria asignada por el programa. Un *bloque cliente* es un tipo de bloque de memoria especial utilizado por programas MFC para objetos que requieren un destructor. El operador `new` de MFC crea un bloque normal o un bloque cliente, según convenga, para el objeto que se está creando.

Un *bloque CRT* es asignado por la biblioteca CRT para su propio uso. La biblioteca de CRT controla la desasignación de estos bloques, por lo que los bloques de CRT no aparecerán en el informe de fuga de memoria a menos que haya problemas graves con la biblioteca de CRT.

Hay otros dos tipos de bloques de memoria que no aparecen nunca en los informes de pérdida de memoria. Un *bloque libre* es memoria que se ha liberado, por lo que, por definición, no se pierde. Un *bloque omitido* es memoria que se ha marcado explícitamente para excluirla del informe de fuga de memoria.

Las técnicas anteriores identifican fugas de memoria para la memoria asignada mediante la función estándar `malloc` de CRT. Sin embargo, si el programa asigna memoria mediante el C++ operador `new`, es posible que solo vea el nombre de archivo y el número de línea donde `operator new` llama a `_malloc_dbg` en el informe de fuga de memoria. Para crear un informe de fuga de memoria más útil, puede escribir una macro como la siguiente para informar de la línea que realizó la asignación:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Ahora, puede reemplazar el operador `new` mediante la macro `DBG_NEW` en el código. En las compilaciones de depuración, `DBG_NEW` usa una sobrecarga de `operator new` global que toma parámetros adicionales para el tipo de bloque, el archivo y el número de línea. La sobrecarga de `new` llama a `_malloc_dbg` para registrar la información adicional. Los informes de fuga de memoria muestran el nombre de archivo y el número de línea donde se asignaron los objetos perdidos. Las compilaciones de versión siguen usando el `new`predeterminado. A continuación se muestra un ejemplo de la técnica:

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

Al ejecutar este código en el depurador de Visual Studio, la llamada a `_CrtDumpMemoryLeaks` genera un informe en la ventana **Salida** que tiene un aspecto similar a este:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Esta salida informa de que la asignación perdida se encontraba en la línea 20 de *debug_new. cpp*.

>[!NOTE]
>No se recomienda crear una macro de preprocesador denominada `new` ni cualquier otra palabra clave de lenguaje.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Establecimiento de puntos de interrupción en un número de asignación de memoria

El número de asignación de memoria le indica cuándo se asignó un bloque de pérdida de memoria. Un bloque con un número de asignación de memoria de 18, por ejemplo, es el decimoctavo bloque de memoria asignado durante la ejecución de la aplicación. El informe de CRT cuenta todas las asignaciones de bloques de memoria durante la ejecución, incluidas las asignaciones de la biblioteca de CRT y otras bibliotecas como MFC. Por lo tanto, el bloque de asignación de memoria número 18 probablemente no es el decimoctavo bloque de memoria asignado por el código.

Puede utilizar el número de asignación para establecer un punto de interrupción en la asignación de memoria.

**Para definir un punto de interrupción de asignación de memoria mediante la ventana Inspección:**

1. Establezca un punto de interrupción cerca del inicio de la aplicación e inicie la depuración.

1. Cuando la aplicación se pausa en el punto de interrupción, abra una ventana **Inspección** seleccionando **Depurar** > **Ventanas** > **Inspección 1** (o **Inspección 2**, **Inspección 3** o **Inspección 4**).

1. En la ventana **Inspección**, escriba `_crtBreakAlloc` en la columna **Nombre**.

   Si está utilizando la versión DLL de subprocesamiento múltiple de la biblioteca de CRT (la opción /MD), agregue el operador de contexto: `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Asegúrese de que se cargan los símbolos de depuración. De lo contrario, se informará de `_crtBreakAlloc` como *no identificado*.

1. Presione **ENTRAR**.

   El depurador evalúa la llamada y coloca el resultado en la columna **Valor** . Este valor será **–1** si no se han definido puntos de interrupción sobre asignaciones de memoria.

1. En la columna **Valor**, reemplace el valor por el número de asignación de la asignación de memoria donde quiere que el depurador realice la interrupción.

Después de establecer un punto de interrupción en un número de asignación de memoria, continúe con la depuración. Asegúrese de que la ejecución se produce en las mismas condiciones, de modo que no cambie el número de asignación de memoria. Cuando el programa se interrumpe en la asignación de memoria especificada, use la ventana **Pila de llamadas** y otras ventanas de depurador para determinar las condiciones en las que se asignó la memoria. A continuación, puede continuar la ejecución para observar qué le ocurre al objeto y determinar por qué no se desasigna correctamente.

También podría resultar útil definir un punto de interrupción de datos sobre el objeto. Para más información, vea [Uso de puntos de interrupción](../debugger/using-breakpoints.md).

También puede establecer puntos de interrupción de asignación de memoria en el código. Puede establecer:

```cpp
_crtBreakAlloc = 18;
```

 O bien

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Comparación de estados de memoria

Otra técnica para localizar pérdidas de memoria requiere tomar instantáneas del estado de la memoria de la aplicación en determinados puntos clave. Para tomar una instantánea del estado de la memoria en un punto determinado de la aplicación, cree una estructura `_CrtMemState` y pásela a la función `_CrtMemCheckpoint`.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

Esta función `_CrtMemCheckpoint` rellena la estructura con una instantánea del estado actual de la memoria.

Para generar el contenido de una estructura `_CrtMemState`, pase la estructura a la función `_ CrtMemDumpStatistics`:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` genera un volcado de memoria del estado de la memoria con esta apariencia:

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

`_CrtMemDifference` compara los estados de la memoria `s1` y `s2`, y devuelve un resultado en (`s3`) que es la diferencia entre `s1` y `s2`.

Una técnica para buscar fugas de memoria empieza realizando llamadas a `_CrtMemCheckpoint` al principio y al final de la aplicación y, a continuación, utilizando `_CrtMemDifference` para comparar los resultados. Si `_CrtMemDifference` muestra una fuga de memoria, puede agregar más llamadas a `_CrtMemCheckpoint` para dividir el programa mediante una búsqueda binaria hasta que haya aislado el origen de la fuga.

## <a name="false-positives"></a>Falsos positivos

 `_CrtDumpMemoryLeaks` puede proporcionar indicaciones falsas de fugas de memoria si una biblioteca marca las asignaciones internas como bloques normales en lugar de bloques de CRT o bloques de cliente. En tal caso, `_CrtDumpMemoryLeaks` no puede distinguir entre las asignaciones del usuario y las asignaciones de la biblioteca internas. Si los destructores globales de las asignaciones de biblioteca se ejecutan después del punto donde se llamó a `_CrtDumpMemoryLeaks`, cada asignación interna de la biblioteca se notifica como pérdida de memoria. Las versiones de la Biblioteca de plantillas estándar anteriores a Visual Studio .NET pueden hacer que `_CrtDumpMemoryLeaks` notifique estos falsos positivos.

## <a name="see-also"></a>Vea también

- [Detalles del montón de depuración de CRT](../debugger/crt-debug-heap-details.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
