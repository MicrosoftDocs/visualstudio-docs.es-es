---
title: Detalles del montón de depuración de CRT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22307c44e4f82056887fadf6e8fde9e1449a19a5
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247938"
---
# <a name="crt-debug-heap-details"></a>Detalles del montón de depuración de CRT
Este tema proporciona un examen detallado del montón de depuración de CRT.

## <a name="contents"></a><a name="BKMK_Contents"></a> Contenido
[Buscar saturaciones de búfer mediante el montón de depuración](#BKMK_Find_buffer_overruns_with_debug_heap)

[Tipos de bloques en el montón de depuración](#BKMK_Types_of_blocks_on_the_debug_heap)

[Comprobar la integridad y pérdidas de memoria del montón](#BKMK_Check_for_heap_integrity_and_memory_leaks)

[Configurar el montón de depuración](#BKMK_Configure_the_debug_heap)

[new, delete y _CLIENT_BLOCKs en el montón de depuración de C++](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)

[Funciones que indican el estado del montón](#BKMK_Heap_State_Reporting_Functions)

[Seguir las solicitudes de asignación en el montón](#BKMK_Track_Heap_Allocation_Requests)

## <a name="find-buffer-overruns-with-debug-heap"></a><a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Buscar saturaciones de búfer mediante el montón de depuración
Dos de los problemas más comunes y difíciles de tratar con los que se encuentran los programadores son la sobrescritura al final de un búfer asignado y las pérdidas de memoria (incapacidad de liberar asignaciones de memoria que ya no se necesitan). El montón de depuración proporciona herramientas eficaces para solucionar este tipo de problemas de asignación de memoria.

Las versiones de depuración de las funciones del montón llaman a las versiones base o estándar utilizadas en las versiones de lanzamiento. Cuando se solicita un bloque de memoria, el administrador del montón de depuración asigna en el montón base un bloque de memoria ligeramente mayor que el solicitado y devuelve un puntero a la parte solicitada. Por ejemplo, suponga que la aplicación contiene la llamada: `malloc( 10 )`. En una versión de lanzamiento, [malloc](/cpp/c-runtime-library/reference/malloc) llamaría a la rutina base de asignación en el montón y solicitaría una asignación de memoria de 10 bytes. Pero en una versión de depuración, `malloc` llamaría a [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg), que, a su vez, llamaría a la rutina base de asignación en el montón y solicitaría una asignación de 10 bytes más unos 36 bytes de memoria adicionales. Todos los bloques de memoria del montón de depuración se encuentran conectados en una lista simplemente vinculada, ordenados según el momento en que fueron asignados.

La memoria adicional asignada por las rutinas del montón de depuración se utiliza para contabilizar información, para punteros que vinculan bloques de memoria de depuración entre sí y para pequeños búferes a cada lado de los datos que permiten capturar sobrescrituras en la región asignada.

Actualmente, la estructura de encabezado de bloque que se utiliza para almacenar esa información de contabilidad del montón se declara en el archivo de encabezado DBGINT.H del siguiente modo:

```cpp
typedef struct _CrtMemBlockHeader
{
// Pointer to the block allocated just before this one:
    struct _CrtMemBlockHeader *pBlockHeaderNext;
// Pointer to the block allocated just after this one:
    struct _CrtMemBlockHeader *pBlockHeaderPrev;
    char *szFileName;    // File name
    int nLine;           // Line number
    size_t nDataSize;    // Size of user block
    int nBlockUse;       // Type of block
    long lRequest;       // Allocation number
// Buffer just before (lower than) the user's memory:
    unsigned char gap[nNoMansLandSize];
} _CrtMemBlockHeader;

/* In an actual memory block in the debug heap,
 * this structure is followed by:
 *   unsigned char data[nDataSize];
 *   unsigned char anotherGap[nNoMansLandSize];
 */
```

Los búferes `NoMansLand`situados a cada lado del área de datos de usuario del bloque ocupan actualmente 4 bytes y se rellenan con un valor de byte conocido utilizado por las rutinas del montón de depuración para comprobar que los límites del bloque de memoria del usuario no se han sobrescrito. El montón de depuración también rellena nuevos bloques de memoria con un valor conocido. Si elige mantener los bloques liberados en la lista vinculada del montón como se explica más adelante, estos bloques liberados se rellenan también con un valor conocido. Comúnmente, los valores de byte utilizados son:

NoMansLand (0xFD): los búferes "NoMansLand", situados a cada lado de la memoria usada por una aplicación, se rellenan con 0xFD.

Bloques liberados (0xDD): los bloques liberados que permanecían sin usar en la lista vinculada del montón de depuración, cuando se establece el marcador `_CRTDBG_DELAY_FREE_MEM_DF`, se rellenan con 0xDD.

Nuevos objetos (0xCD): los objetos nuevos se rellenan con 0xCD al asignarse.

![Volver al principio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)

## <a name="types-of-blocks-on-the-debug-heap"></a><a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Tipos de bloques en el montón de depuración
Cada bloque de memoria del montón de depuración se asigna a uno de entre cinco tipos de asignación. Estos tipos reciben un seguimiento y se informa de ellos de forma diferente en cuanto a detección de pérdidas e informe de estados. El tipo de un bloque se puede especificar asignándolo mediante una llamada directa a una de las funciones de asignación del montón de depuración, como [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Los cinco tipos de bloques de memoria del montón de depuración (definidos en el miembro **nBlockUse** de la estructura **_CrtMemBlockHeader**) son los siguientes:

**_NORMAL_BLOCK**: una llamada a [malloc](/cpp/c-runtime-library/reference/malloc) o [calloc](/cpp/c-runtime-library/reference/calloc) crea un bloque Normal. Si se pretende utilizar sólo bloques de tipo Normal y no se necesitan bloques de tipo Cliente, es recomendable definir [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), que hace que todas las llamadas de asignación en el montón se asignen a sus equivalentes de depuración en el caso de versiones de depuración. Esto permite almacenar la información de nombre de archivo y número de línea para cada llamada de asignación en el encabezado de bloque correspondiente.

`_CRT_BLOCK` Los bloques de memoria asignados internamente por muchas de las funciones de la biblioteca en tiempo de ejecución se marcan como bloques CRT, de modo que se puedan controlar por separado. Como resultado de ello, la detección de pérdidas de memoria, así como otras operaciones, no tienen por qué verse afectadas. En una asignación de memoria, nunca se debe asignar, reasignar o liberar ningún bloque de tipo CRT.

`_CLIENT_BLOCK` Una aplicación puede mantener un seguimiento especial de un determinado grupo de asignaciones de memoria, a efectos de depuración, si las asigna con este tipo de bloque de memoria y utiliza llamadas explícitas para las funciones del montón de depuración. MFC, por ejemplo, asigna todos los **CObjects** como bloques de tipo Cliente; otras aplicaciones podrían mantener diferentes objetos de memoria en bloques Cliente. Asimismo, se pueden especificar subtipos de bloques Cliente para conseguir un mayor detalle en el seguimiento. Si desea especificar subtipos de bloques Cliente, desplace el número 16 bits a la izquierda y súmelo, mediante la operación lógica `OR`, con `_CLIENT_BLOCK`. Por ejemplo:

```cpp
#define MYSUBTYPE 4
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));
```

Una función de enlace suministrada por el cliente para realizar un volcado de los objetos almacenados en bloques Cliente se puede instalar mediante [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient); se llamará a esta función siempre que una función de depuración realice un volcado de un bloque Cliente. Asimismo, [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects) se puede utilizar para llamar a una función dada suministrada por la aplicación para cada bloque Cliente del montón de depuración.

**_FREE_BLOCK**: normalmente, los bloques que se han liberado se quitan de la lista. Para comprobar que aún no se está escribiendo en la memoria liberada, o para simular un estado de escasez de memoria, se puede optar por mantener los bloques liberados en la lista vinculada, marcados como Libres y rellenos con un valor de byte conocido (actualmente 0xDD).

**_IGNORE_BLOCK**: es posible desactivar las operaciones del montón de depuración durante un período de tiempo. En este período, los bloques de memoria se mantienen en la lista, pero se marcan como bloques Omitir.

Para determinar el tipo y subtipo de un bloque dado, utilice la función [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) y las macros **_BLOCK_TYPE** y **_BLOCK_SUBTYPE**. Las macros se definen (en crtdbg.h) del siguiente modo:

```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)
```

![Volver al principio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)

## <a name="check-for-heap-integrity-and-memory-leaks"></a><a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Comprobar la integridad y pérdidas de memoria del montón
El acceso a muchas de las características del montón de depuración se debe realizar desde dentro del código. En la sección siguiente se describen algunas características y cómo utilizarlas.

`_CrtCheckMemory` Se puede utilizar una llamada a [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory), por ejemplo, para comprobar la integridad del montón en cualquier punto. Esta función examina cada bloque de memoria del montón, comprueba si la información de encabezado del bloque de memoria es válida y confirma que los búferes no se hayan modificado.

`_CrtSetDbgFlag` Se puede controlar cómo el montón de depuración hace un seguimiento de las asignaciones utilizando un marcador interno, [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag), que se puede leer y definir mediante la función [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag). Cambiando este marcador, se puede indicar al montón de depuración que compruebe si existen pérdidas de memoria cuando el programa termina, e informa de las pérdidas detectadas. Análogamente, se puede especificar que los bloques de memoria liberada no se quiten de la lista vinculada para simular situaciones de escasez de memoria. Cuando se comprueba el montón, estos bloques liberados se examinan en su totalidad para asegurarse de que no se han modificado.

El marcador **_crtDbgFlag** contiene los siguientes campos de bit:

|Campo de bit|Default<br /><br /> value|Descripción|
|---------------|-----------------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|Activado|Activa la asignación para depuración. Cuando este bit está desactivado, las asignaciones permanecen vinculadas entre sí, pero su tipo de bloque es **_IGNORE_BLOCK**.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|Desactivado|Impide la liberación real de memoria, como en la simulación del estado de memoria escasa. Cuando este bit está activado, los bloques liberados se mantienen en la lista vinculada del montón de depuración, pero se marcan como **_FREE_BLOCK** y se rellenan con un valor de byte especial.|
|**_CRTDBG_CHECK_ALWAYS_DF**|Desactivado|Hace que se llame a **_CrtCheckMemory** en cada asignación y desasignación. Esto ralentiza la ejecución, pero permite capturar los errores rápidamente.|
|**_CRTDBG_CHECK_CRT_DF**|Desactivado|Hace que los bloques marcados con el tipo **_CRT_BLOCK** se incluyan en las operaciones de detección de pérdidas y de diferencia de estado. Cuando este bit está desactivado, la memoria utilizada internamente por la biblioteca en tiempo de ejecución se omite durante esas operaciones.|
|**_CRTDBG_LEAK_CHECK_DF**|Desactivado|Hace que la comprobación de pérdidas se realice a la salida del programa mediante una llamada a **_CrtDumpMemoryLeaks**. Si la aplicación no consigue liberar toda la memoria asignada, se genera un informe de error.|

![Volver al principio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)

## <a name="configure-the-debug-heap"></a><a name="BKMK_Configure_the_debug_heap"></a> Configurar el montón de depuración
Todas las llamadas a funciones del montón, como `malloc`, `free`, `calloc`, `realloc`, `new` y `delete`, se resuelven en versiones de depuración de esas funciones que operan sobre el montón de depuración. Cuando se libera un bloque de memoria, el montón de depuración comprueba automáticamente la integridad de los búferes situados a cada lado del área asignada y emite un informe de error en caso de sobrescritura.

**Para utilizar el montón de depuración**

- Vincule la versión de depuración de la aplicación con una versión de depuración de la biblioteca en tiempo de ejecución de C.

  **Para cambiar campos de bit _crtDbgFlag y crear un nuevo estado para el marcador**

1. Llame a `_CrtSetDbgFlag` con el parámetro `newFlag` definido como `_CRTDBG_REPORT_FLAG` (para obtener el estado actual de `_crtDbgFlag`) y almacene el valor devuelto en una variable temporal.

2. Puede activar cualquier bit haciendo la operación `OR` (símbolo &#124; bit a bit) de la variable temporal con la máscara de bits correspondiente (representada en el código de la aplicación mediante constantes del manifiesto).

3. Desactive los demás bits aplicando la operación `AND` (símbolo & bit a bit) a la variable con `NOT` (símbolo ~ bit a bit) de la máscara de bits apropiada.

4. Llame a `_CrtSetDbgFlag` con el parámetro `newFlag` establecido en el valor almacenado en la variable temporal para crear el nuevo estado de `_crtDbgFlag`.

   Por ejemplo, las siguientes líneas de código activan automáticamente la detección de pérdidas y desactivan la comprobación de bloques de tipo `_CRT_BLOCK`:

```cpp
// Get current flag
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn on leak-checking bit.
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;

// Turn off CRT block checking bit.
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;

// Set flag to the new value.
_CrtSetDbgFlag( tmpFlag );
```

![Volver al principio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)

## <a name="new-delete-and-_client_blocks-in-the-c-debug-heap"></a><a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> new, delete y \_CLIENT\_BLOCKs en el montón de depuración de C++
Las versiones de depuración de la biblioteca en tiempo de ejecución de C contienen versiones de depuración de los operadores `new` y `delete` de C++. Si usa el tipo de asignación `_CLIENT_BLOCK`, debe llamar a la versión de depuración del operador `new` directamente o crear macros que reemplacen al operador `new` en modo de depuración, como se muestra en el siguiente ejemplo:

```cpp
/* MyDbgNew.h
 Defines global operator new to allocate from
 client blocks
*/

#ifdef _DEBUG
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)
#else
   #define DEBUG_CLIENTBLOCK
#endif // _DEBUG

/* MyApp.cpp
        Use a default workspace for a Console Application to
 *      build a Debug version of this code
*/

#include "crtdbg.h"
#include "mydbgnew.h"

#ifdef _DEBUG
#define new DEBUG_CLIENTBLOCK
#endif

int main( )   {
    char *p1;
    p1 =  new char[40];
    _CrtMemDumpAllObjectsSince( NULL );
}
```

La versión de depuración del operador `delete` funciona con todos los tipos de bloques y no requiere realizar cambios en el programa cuando se compila una versión de lanzamiento.

![Volver al principio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)

## <a name="heap-state-reporting-functions"></a><a name="BKMK_Heap_State_Reporting_Functions"></a> Funciones que indican el estado del montón
 **_CrtMemState**

 Para capturar una instantánea resumen del estado del montón en un instante determinado, use la estructura _CrtMemState definida en CRTDBG.H:

```cpp
typedef struct _CrtMemState
{
    // Pointer to the most recently allocated block:
    struct _CrtMemBlockHeader * pBlockHeader;
    // A counter for each of the 5 types of block:
    size_t lCounts[_MAX_BLOCKS];
    // Total bytes allocated in each block type:
    size_t lSizes[_MAX_BLOCKS];
    // The most bytes allocated at a time up to now:
    size_t lHighWaterCount;
    // The total bytes allocated at present:
    size_t lTotalCount;
} _CrtMemState;
```

Esta estructura guarda un puntero al primer bloque (el más recientemente asignado) en la lista vinculada del montón de depuración. A continuación, registra en dos matrices cuántos bloques de cada tipo de bloque de memoria (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK, etc.) hay en la lista, así como el número de bytes asignados en cada tipo de bloque. Por último, registra el mayor número de bytes asignado en el montón de manera global hasta ese punto y el número de bytes asignado actualmente.

**Otras funciones CRT para informes**

Las siguientes funciones informan del estado y el contenido del montón, y utilizan la información para ayudar a detectar pérdidas de memoria y otros problemas.

|Función|Descripción|
|--------------|-----------------|
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Guarda una instantánea del montón en una estructura **_CrtMemState** proporcionada por la aplicación.|
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|Compara dos estructuras de estados de memoria, guarda la diferencia entre ellas en una tercera estructura de estado y devuelve TRUE si los dos estados son diferentes.|
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Realiza un volcado de memoria de una estructura **_CrtMemState** dada. La estructura puede contener una instantánea del estado del montón de depuración en un momento dado, o la diferencia entre dos instantáneas.|
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Realiza un volcado de memoria de información de todos los objetos asignados desde que se tomó una determinada instantánea del montón o desde el inicio de la ejecución. Cada vez que vuelca un bloque **_CLIENT_BLOCK**, llama a una función de enlace suministrada por la aplicación, si se instaló una mediante **_CrtSetDumpClient**.|
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Determina si se produjo alguna pérdida de memoria desde el inicio de la ejecución del programa; en ese caso, realiza un volcado de memoria de todos los objetos asignados. Cada vez que **_CrtDumpMemoryLeaks** vuelca un bloque **_CLIENT_BLOCK**, llama a una función de enlace suministrada por la aplicación, si se instaló una mediante **_CrtSetDumpClient**.|

![Volver al principio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)

## <a name="track-heap-allocation-requests"></a><a name="BKMK_Track_Heap_Allocation_Requests"></a> Seguir las solicitudes de asignación en el montón
Aunque la determinación exacta del nombre del archivo de código fuente y el número de línea en el que una aserción o una macro de informe se ejecuta suele ser muy útil para localizar la causa de un problema, esto no es aplicable siempre en el caso de funciones de asignación de memoria en el montón. Mientras que las macros se pueden insertar en muchos puntos apropiados del árbol lógico de una aplicación, una asignación de memoria se suele incluir en una rutina especial a la que se llama desde muchos sitios diferentes y en muchos momentos diferentes. Normalmente, la cuestión no es qué línea de código realizó una asignación incorrecta, sino cuál de las miles de asignaciones efectuadas por esa línea de código fue incorrecta y por qué.

**Números de solicitud de asignación únicos y _crtBreakAlloc**

La manera más simple de identificar la llamada de asignación incorrecta consiste en aprovechar el número de solicitud de asignación único asociado con cada bloque del montón de depuración. Cuando alguna de las funciones de volcado de memoria proporciona información sobre un bloque, este número de solicitud de asignación aparece encerrado entre llaves (por ejemplo, "{36}").

Una vez que se conoce el número de solicitud de asignación de un bloque asignado incorrectamente, se puede pasar este número a [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) para crear un punto de interrupción. La ejecución se interrumpe justo antes de asignar el bloque y se puede realizar un seguimiento hacia atrás para determinar qué rutina fue la responsable de la llamada errónea. Para evitar tener que volver a compilar, se puede conseguir lo mismo en el depurador si se asigna a **_crtBreakAlloc** el número de solicitud de asignación que interesa.

**Crear versiones de depuración de sus rutinas de asignación**

Un enfoque algo más complicado consiste en crear versiones de depuración de las propias rutinas de asignación, comparables a las versiones **_dbg** de las [funciones de asignación en el montón](../debugger/debug-versions-of-heap-allocation-functions.md). A continuación, se pueden pasar como argumentos el archivo de código fuente y el número de línea a las rutinas subyacentes de asignación en el montón; entonces, se podrá ver inmediatamente dónde se originó cualquier asignación incorrecta.

Por ejemplo, suponga que la aplicación contiene una rutina utilizada habitualmente similar a la siguiente:

```cpp
int addNewRecord(struct RecStruct * prevRecord,
                 int recType, int recAccess)
{
    // ...code omitted through actual allocation...
    if ((newRec = malloc(recSize)) == NULL)
    // ... rest of routine omitted too ...
}
```

En un archivo de encabezado, se podría agregar código como el siguiente:

```cpp
#ifdef _DEBUG
#define  addNewRecord(p, t, a) \
            addNewRecord(p, t, a, __FILE__, __LINE__)
#endif
```

A continuación, se podría cambiar la asignación en la rutina de creación de registros del siguiente modo:

```cpp
int addNewRecord(struct RecStruct *prevRecord,
                int recType, int recAccess
#ifdef _DEBUG
               , const char *srcFile, int srcLine
#endif
    )
{
    /* ... code omitted through actual allocation ... */
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,
            srcFile, scrLine)) == NULL)
    /* ... rest of routine omitted too ... */
}
```

Ahora, el nombre del archivo de código fuente y el número de línea donde se llamó a `addNewRecord` se almacenarán en cada bloque resultante asignado en el montón de depuración y se informará de ellos al examinar el bloque.

![Volver al principio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)

## <a name="see-also"></a>Vea también
[Depuración de código nativo](../debugger/debugging-native-code.md)
