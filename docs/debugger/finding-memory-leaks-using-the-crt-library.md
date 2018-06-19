---
title: Buscar pérdidas de memoria con la biblioteca CRT | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d858b6c67893e49b4d4e9ec87c3b20fce56dd7c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477867"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Buscar pérdidas de memoria con la biblioteca de CRT
Las pérdidas de memoria, definidas como la incapacidad de desasignar correctamente memoria asignada previamente, se encuentran entre los errores más sutiles y difíciles de detectar en las aplicaciones de C/C++. Una pequeña pérdida de memoria puede no advertirse al principio, pero con el tiempo, una progresiva pérdida de memoria puede producir síntomas que van desde una disminución del rendimiento hasta el bloqueo cuando la aplicación se queda sin memoria. Peor aún, una aplicación con pérdida de memoria que utilice toda la memoria disponible puede hacer que se bloquee otra aplicación, creando confusión respecto a qué aplicación es la responsable. Incluso unas pérdidas de memoria aparentemente inocuas podrían ser síntomas de otros problemas que se deben corregir.  
  
 El depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y las bibliotecas en tiempo de ejecución de C (CRT) proporcionan medios para detectar e identificar las pérdidas de memoria.  
  
## <a name="enabling-memory-leak-detection"></a>Habilitar la detección de pérdidas de memoria  
 Las herramientas principales para detectar pérdidas de memoria son el depurador y las funciones del montón de depuración de las bibliotecas en tiempo de ejecución de C (CRT).  
  
 Para habilitar las funciones del montón de depuración, incluya las siguientes instrucciones en el programa:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Para que las funciones CRT funcionen correctamente, las instrucciones `#include` deben seguir el orden que se muestra aquí.  
  
 Si se incluye crtdbg.h, se asignan las funciones `malloc` y [free](/cpp/c-runtime-library/reference/free) a sus versiones de depuración [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) y `free`, que realizan un seguimiento de la asignación y desasignación de memoria. Esta asignación se produce únicamente en las compilaciones de depuración, que tienen `_DEBUG`. Las versiones de lanzamiento utilizan las funciones normales `malloc` y `free` .  
  
 La instrucción `#define` asigna una versión base de las funciones del montón de CRT a la versión de depuración correspondiente. Si omite la instrucción `#define` , el volcado de pérdida de memoria será menos detallado.  
  
 Después de haber habilitado las funciones del montón mediante estas instrucciones, puede realizar una llamada a `_CrtDumpMemoryLeaks` antes de un punto de salida de la aplicación para mostrar un informe de pérdida de memoria cuando se cierre la aplicación:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Si su aplicación tiene varias salidas, no es necesario realizar manualmente una llamada a [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) en cada punto de salida. Una llamada a `_CrtSetDbgFlag` al principio de la aplicación producirá una llamada automática a `_CrtDumpMemoryLeaks` en cada punto de salida. Debe establecer los campos de dos bits que se muestran aquí:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 De forma predeterminada, `_CrtDumpMemoryLeaks` genera el informe de pérdida de memoria en el panel de **Depuración** de la **Ventana de salida** . Puede utilizar `_CrtSetReportMode` para redirigir el informe a otra ubicación.  
  
 Si utiliza una biblioteca, esta podría hacer que se envíen los resultados a otra ubicación. En ese caso, puede volver a establecer la ubicación de salida en la **Ventana de salida** , como se muestra aquí:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretar el informe de pérdida de memoria  
 Si la aplicación no define `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) muestran un informe de pérdida de memoria con esta apariencia:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Si la aplicación define `_CRTDBG_MAP_ALLOC`, el informe de pérdida de memoria tiene el siguiente aspecto:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 La diferencia es que el segundo informe muestra el nombre del archivo y el número de línea en el que se asigna primero la pérdida memoria.  
  
 Tanto si define o no `_CRTDBG_MAP_ALLOC` , el informe de pérdida de memoria mostrará la siguiente información:  
  
-   El número de asignación de memoria, que es `18` en este ejemplo  
  
-   El [tipo de bloque](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97), que es `normal` en este ejemplo.  
  
-   La ubicación de memoria hexadecimal, que es `0x00780E80` en este ejemplo.  
  
-   El tamaño del bloque, `64 bytes` en este ejemplo.  
  
-   Los primeros 16 bytes de datos del bloque, en formato hexadecimal.  
  
 El informe de pérdida de memoria identifica un bloque de memoria como normal, cliente o CRT. Un *bloque normal* se compone de memoria ordinaria asignada por el programa. Un *bloque cliente* es un tipo de bloque de memoria especial utilizado por programas MFC para objetos que requieren un destructor. El operador `new` de MFC crea un bloque normal o un bloque cliente, según convenga, para el objeto que se está creando. Un *bloque CRT* es asignado por la biblioteca CRT para su propio uso. La biblioteca CRT controla la desasignación de estos bloques. Por consiguiente, es improbable que los vea en el informe de pérdida de memoria, a menos que exista algún problema serio, por ejemplo, que la biblioteca CRT esté dañada.  
  
 Hay otros dos tipos de bloques de memoria que no aparecen nunca en los informes de pérdida de memoria. Un *bloque libre* es un bloque de memoria que se ha liberado. Eso significa que no está perdida, por definición. Un *bloque omitido* es memoria que se ha marcado explícitamente para excluirla del informe de pérdida de memoria.  
  
 Estas técnicas funcionan para la memoria asignada mediante la función `malloc` de CRT estándar. Si el programa asigna memoria mediante C++ `new` (operador), sin embargo, sólo podrá ver el archivo y número de línea donde la implementación global `operator new` llamadas `_malloc_dbg` en el informe de pérdida de memoria. Dado que este comportamiento no es muy útil, puede cambiarlo para informar de la línea que realizó la asignación mediante el uso de una macro que se ve así: 
 
```C++  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Ahora puede reemplazar la `new` operador mediante el uso de la `DBG_NEW` macro en el código. En las compilaciones de depuración, se usa una sobrecarga de global `operator new` que toma parámetros adicionales para el tipo de bloque, el archivo y el número de línea. Esta sobrecarga de `new` llamadas `_malloc_dbg` para registrar la información adicional. Cuando usas `DBG_NEW`, la pérdida de memoria informes muestran el nombre de archivo y número de línea donde se asignaron los objetos perdidos. En las compilaciones comerciales, usa el valor predeterminado `new`. (No se recomienda crear una macro de preprocesador denominada `new`, o cualquier otra palabra clave del lenguaje.) Este es un ejemplo de la técnica:  
  
```C++  
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
  
Al ejecutar este código en el depurador de Visual Studio, la llamada a `_CrtDumpMemoryLeaks` genera un informe en el **salida** ventana que tiene un aspecto similar al siguiente:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Esto indica que la asignación perdida estaba en línea 20 de debug_new.cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Establecer puntos de interrupción en un número de asignación de memoria  
 El número de asignación de memoria le indica cuándo se asignó un bloque de pérdida de memoria. Un bloque con un número de asignación de memoria de 18, por ejemplo, es el decimoctavo bloque de memoria asignado durante la ejecución de la aplicación. El informe de CRT cuenta todas las asignaciones de bloques de memoria durante la ejecución. Esto incluye las asignaciones de la biblioteca CRT y otras bibliotecas como MFC. Por consiguiente, un bloque con un número de asignación de memoria de 18 puede no ser el decimoctavo bloque de memoria asignado por el código. Normalmente, no lo será.  
  
 Puede utilizar el número de asignación para establecer un punto de interrupción en la asignación de memoria.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Para definir un punto de interrupción de asignación de memoria mediante la ventana Inspección  
  
1.  Establezca un punto de interrupción cerca del inicio de la aplicación e iníciela.  
  
2.  Cuando la aplicación se interrumpe en el punto de interrupción, la ventana **Inspección** .  
  
3.  En la ventana **Inspección** , escriba `_crtBreakAlloc` en la columna **Nombre** .  
  
     Si está utilizando la versión DLL de subprocesamiento múltiple de la biblioteca CRT (la opción /MD), incluya el operador de contexto: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4.  Presione **RETORNO**.  
  
     El depurador evalúa la llamada y coloca el resultado en la columna **Valor** . Este valor será -1 si no ha configurado ningún punto de interrupción sobre asignaciones de memoria.  
  
5.  En la columna **Valor** reemplace el valor que se muestra por el número de asignación de la ubicación de memoria donde desea realizar la interrupción.  
  
 Después de establecer un punto de interrupción en un número de asignación de memoria, puede continuar con la depuración. Debe ejecutar el programa bajo las mismas condiciones que la ejecución anterior, de modo que el orden de asignación de memoria no cambie. Cuando el programa se interrumpe en la asignación de memoria especificada, puede usar la ventana **Pila de llamadas** y otras ventanas de depurador para determinar las condiciones en las que se asignó la memoria. A continuación, puede continuar la ejecución para observar qué le ocurre al objeto y determinar por qué no se desasigna correctamente.  
  
 También podría resultar útil definir un punto de interrupción de datos sobre el objeto. Para obtener más información, consulta [Using Breakpoints](../debugger/using-breakpoints.md).  
  
 También puede establecer puntos de interrupción de asignación de memoria en el código. Existen dos modos para hacer esto:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 O bien  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Comparar diferentes estados de memoria  
 Otra técnica para localizar pérdidas de memoria requiere tomar instantáneas del estado de la memoria de la aplicación en determinados puntos clave. Para tomar una instantánea del estado de la memoria en un punto determinado de la aplicación, cree una estructura **_CrtMemState** y pásela a la función `_CrtMemCheckpoint` . Esta función rellena la estructura con una instantánea del estado actual de la memoria:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` rellena la estructura con una instantánea del estado actual de la memoria.  
  
 Para generar el contenido de una estructura **_CrtMemState** , pase la estructura a la función `_ CrtMemDumpStatistics` :  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` genera un volcado de memoria del estado de la memoria con esta apariencia:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Para determinar si se ha producido una pérdida de memoria en una sección de código, puede tomar instantáneas del estado de la memoria antes y después de la sección y, a continuación, utilizar `_ CrtMemDifference` para comparar los dos estados:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` compara los estados de la memoria `s1` y `s2` y devuelve un resultado en (`s3`) que es la diferencia de `s1` y `s2`.  
  
 Una técnica para buscar pérdidas de memoria empieza realizando llamadas a `_CrtMemCheckpoint` al principio y al final de la aplicación y, a continuación, utilizando `_CrtMemDifference` para comparar los resultados. Si `_CrtMemDifference` muestra una pérdida de memoria, puede agregar más llamadas a `_CrtMemCheckpoint` para dividir el programa mediante una búsqueda binaria hasta que haya aislado el origen de la pérdida.  
  
## <a name="false-positives"></a>Falsos positivos  
 En algunos casos, `_CrtDumpMemoryLeaks` puede ofrecer indicaciones falsas de pérdidas de memoria. Esto podría ocurrir si se usa una biblioteca que marca las asignaciones internas como _NORMAL_BLOCK en lugar de como `_CRT_BLOCK`o `_CLIENT_BLOCK`. En tal caso, `_CrtDumpMemoryLeaks` no puede distinguir entre las asignaciones del usuario y las asignaciones de la biblioteca internas. Si los destructores globales de las asignaciones de biblioteca se ejecutan después del punto donde se llamó a `_CrtDumpMemoryLeaks`, cada asignación interna de la biblioteca se notifica como pérdida de memoria. Las versiones de la Biblioteca de plantillas estándar anteriores a Visual Studio .NET, hacían que `_CrtDumpMemoryLeaks` notificase pérdidas de memoria falsas, pero esto se ha solucionado en versiones más recientes.  
  
## <a name="see-also"></a>Vea también  
 [Detalles del montón de depuración de CRT](../debugger/crt-debug-heap-details.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)
