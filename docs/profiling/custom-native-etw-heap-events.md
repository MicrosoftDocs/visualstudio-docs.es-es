---
title: "Eventos de montón ETW nativos personalizados | Microsoft Docs"
ms.custom: 
ms.date: 02/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 7d55fdb061b9cb2fcd0497b7dde8e5c4255cf5e3
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="custom-native-etw-heap-events"></a>Eventos de montón ETW nativos personalizados

Visual Studio contiene diversas [herramientas de diagnóstico y de generación de perfiles](../profiling/profiling-tools.md), incluido un generador de perfiles de memoria nativa.  Este generador de perfiles enlaza los [eventos ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) del proveedor de montón y proporciona un análisis de la manera en que la memoria se asigna y se usa.  De forma predeterminada, esta herramienta solo puede analizar las asignaciones realizadas desde el montón de Windows estándar y no se mostrarán las asignaciones que se encuentran fuera de este montón nativo.

Hay muchos casos en los que podría interesarle usar su propio montón personalizado y evitar la sobrecarga de asignación del montón estándar.  Por ejemplo, puede usar [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) para asignar una gran cantidad de memoria cuando se inicia la aplicación o el juego y, después, administrar sus propios bloques dentro de esa lista.  En este escenario, la herramienta de generador de perfiles de memoria solo vería esa asignación inicial y no la administración personalizada realizada dentro del bloque de memoria.  En cambio, mediante el uso del proveedor ETW de montón nativo personalizado, puede dejar que la herramienta conozca las asignaciones que realiza fuera del montón estándar.

Por ejemplo, en un proyecto similar al siguiente, donde `MemoryPool` es un montón personalizado, solo vería una única asignación en el montón de Windows:

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes 
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

En una instantánea de la herramienta [Uso de memoria](../profiling/memory-usage.md) sin el seguimiento del montón personalizado, solo se mostraría la asignación de 8192 bytes y ninguna de las asignaciones personalizadas realizadas por el grupo:

![Asignación del montón de Windows](media/heap-example-windows-heap.png)

Mediante los pasos siguientes, podemos usar esta misma herramienta para realizar un seguimiento del uso de memoria en el montón personalizado.

## <a name="how-to-use"></a>Cómo se usa

Esta biblioteca se puede usar fácilmente en C y C++.

1. Incluya el encabezado para el proveedor ETW de montón personalizado:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Agregue el elemento Decorator `__declspec(allocator)` a cualquier función del administrador de montones personalizados que devuelva un puntero a la memoria de montón recién asignada.  Este elemento Decorator permite que la herramienta identifique correctamente el tipo de la memoria que se devuelve.  Por ejemplo:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```
   
   > [!NOTE]
   > Este elemento Decorator le indica al compilador que esta función es una llamada a un asignador.  Cada llamada a la función dará como resultado la dirección del sitio de llamada, el tamaño de la instrucción de llamada y el identificador de tipo del nuevo objeto en un nuevo símbolo `S_HEAPALLOCSITE`.  Cuando se asigna una pila de llamadas, Windows emite un evento ETW con esta información.  La herramienta de generador de perfiles de memoria recorre la pila de llamadas en busca de una dirección de devolución que coincida con un símbolo `S_HEAPALLOCSITE`, y la información del identificador de tipo del símbolo se usa para mostrar el tipo de tiempo de ejecución de la asignación.
   >
   > En resumen, esto significa que una llamada similar a `(B*)(A*)MyMalloc(sizeof(B))` se mostrará en la herramienta como si fuera de tipo `B`, no `void` o `A`.

1. Para C++, cree el objeto `VSHeapTracker::CHeapTracker` y asígnele un nombre al montón, que se mostrará en la herramienta de generación de perfiles:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Si usa C, use la función `OpenHeapTracker`.  Esta función devuelve un identificador que usará cuando realice una llamada a otras funciones de seguimiento:
  
   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Cuando asigne memoria mediante la función personalizada, llame al método `AllocateEvent` (C++) o `VSHeapTrackerAllocateEvent` (C) y pase el puntero a la memoria y su tamaño para realizar un seguimiento de la asignación:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   o

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > No olvide etiquetar la función de asignador personalizado con el elemento Decorator `__declspec(allocator)` descrito anteriormente.

1. Cuando desasigne memoria mediante la función personalizada, llame a la función `DeallocateEvent` (C++) o `VSHeapTracerDeallocateEvent` (C) y pase el puntero a la memoria para realizar un seguimiento de la desasignación:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   O bien

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Cuando reasigne memoria mediante la función personalizada, llame al método `ReallocateEvent` (C++) o `VSHeapReallocateEvent` (C), pase un puntero a la memoria nueva y al tamaño de la asignación, y pase un puntero a la memoria antigua:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   O bien

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Por último, para cerrar y limpiar el rastreador de montón personalizado en C++, use el destructor `CHeapTracker`, ya sea manualmente o a través de reglas de ámbito estándar, o la función `CloseHeapTracker` en C:

   ```cpp
   delete pHeapTracker;
   ```

   O bien

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="tracking-memory-usage"></a>Seguimiento del uso de la memoria
Una vez realizadas estas llamadas, se puede realizar un seguimiento del uso del montón personalizado mediante la herramienta estándar **Uso de memoria** en Visual Studio.  Para obtener más información sobre cómo usar esta herramienta, vea la documentación sobre el [uso de memoria](../profiling/memory-usage.md). Asegúrese de que ha habilitado la generación de perfiles de montón con instantáneas. En caso contrario, no verá el uso del montón personalizado. 

![Habilitar la generación de perfiles de montón](media/heap-enable-heap.png)

Para ver el seguimiento del montón personalizado, use la lista desplegable **Montón** situada en la esquina superior derecha de la ventana **Instantánea** para cambiar la vista del *Montón de NT* a su propio montón, con el nombre que le ha asignado anteriormente.

![Selección del montón](media/heap-example-custom-heap.png)

Mediante el ejemplo de código anterior, en el que `MemoryPool` crea un objeto `VSHeapTracker::CHeapTracker`, y nuestro propio método `allocate` que llama al método `AllocateEvent`, ahora puede ver el resultado de esa asignación personalizada, que muestra tres instancias con un total de 24 bytes, todas de tipo `Foo`.

El montón predeterminado *Montón de NT* tiene el mismo aspecto que antes, pero se le ha agregado el objeto `CHeapTracker`.

![Montón de NT con el rastreador](media/heap-example-windows-heap.png)

Al igual que en el montón de Windows estándar, también puede usar esta herramienta para comparar instantáneas y buscar fugas y daños en el montón personalizado. Esto se describe en la documentación principal sobre el [uso de memoria](../profiling/memory-usage.md).

> [!TIP]
> Visual Studio también contiene una herramienta **Uso de memoria** en el conjunto de herramientas **Generación de perfiles de rendimiento**, que se habilita en la opción de menú **Depurar > Generador de perfiles de rendimiento** o mediante la combinación de teclado **ALT+F2**.  Esta característica no incluye el seguimiento del montón y no mostrará el montón personalizado como se describe aquí.  Esta funcionalidad solo está incluida en la ventana **Herramientas de diagnóstico**, que se puede habilitar en el menú **Depurar > Windows > Mostrar herramientas de diagnóstico** o mediante la combinación de teclado **Ctrl+Alt+F2**.

## <a name="see-also"></a>Vea también
[Herramientas de generación de perfiles](../profiling/profiling-tools.md)  
[Uso de memoria](../profiling/memory-usage.md)
