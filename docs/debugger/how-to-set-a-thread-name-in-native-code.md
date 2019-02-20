---
title: 'Cómo: establecer un nombre de subproceso en código nativo | Microsoft Docs'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c547dd00f7a5a31b949d22c13f305050355207c7
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227321"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Cómo: Establecer un nombre de subproceso en código nativo
La denominación de los subprocesos es posible en cualquier edición de Visual Studio. Denominación de los subprocesos es útil para identificar los subprocesos de interés en el **subprocesos** ventana cuando se depura un proceso en ejecución. Denominado reconozca los subprocesos también pueden ser útil al realizar la depuración post-mortem a través de la inspección de volcado de bloqueo y al analizar el rendimiento de captura mediante distintas herramientas.

## <a name="ways-to-set-a-thread-name"></a>Maneras de establecer un nombre de subproceso

Hay dos maneras de establecer un nombre de subproceso. La primera es a través de la [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) función. La segunda es producir una excepción determinada mientras el depurador de Visual Studio se adjunta al proceso. Cada enfoque tiene ventajas y las advertencias.

Es importante destacar que _ambos_ enfoques pueden usarse conjuntamente, si lo desea, ya que los mecanismos que funcionan son independientes entre sí.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Establecer un nombre de subproceso mediante `SetThreadDescription`

Ventajas:
* Nombres de subprocesos están visibles cuando se depura en Visual Studio, independientemente de si el depurador se asoció al proceso en el momento en que se invoca SetThreadDescription.
* Nombres de subprocesos son visibles al realizar la depuración post-mortem cargando un archivo de volcado en Visual Studio.
* Nombres de subprocesos también son visibles al usar otras herramientas, como el [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) depurador y el [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) analizador de rendimiento.

Advertencias:
* Nombres de subprocesos sólo están visibles en Visual Studio 2017 versión 15.6 y versiones posteriores.
* Cuando el archivo de volcado de depuración de un bloqueo de post mortem, nombres de subproceso solo son visibles si el bloqueo se creó en Windows 10 versión 1607, Windows Server 2016 o versiones posteriores de Windows.

*Ejemplo:*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Establecer un nombre de subproceso iniciando una excepción

Es otra forma de establecer un nombre de subproceso en el programa se comunique el nombre deseado del subproceso al depurador de Visual Studio iniciando una excepción especialmente configurado.

Ventajas:
* Funciona en todas las versiones de Visual Studio.

Advertencias:
* Solo funciona si el depurador se adjunta en el momento en que se usa el método basado en excepciones.
* Nombres de subprocesos que se establece mediante el uso de este método no estará disponibles en los volcados de memoria o las herramientas de análisis de rendimiento.

*Ejemplo:*

El `SetThreadName` función que se muestra a continuación muestra este enfoque basado en excepciones. Tenga en cuenta que el nombre del subproceso se copiarán automáticamente al subproceso, para que la memoria para el `threadName` parámetro puede liberarse tras el `SetThreadName` se complete la llamada.

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>Vea también
[Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)  
[Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)  
[Cómo: Establecer un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md)
