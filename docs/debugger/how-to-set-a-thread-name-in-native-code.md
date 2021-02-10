---
title: Establecimiento de un nombre de subproceso en código nativo | Microsoft Docs
description: Establezca un nombre de subproceso en código nativo durante la depuración de aplicaciones multiproceso en Visual Studio. La denominación de los subprocesos se usa para hacer el seguimiento en la ventana Subprocesos.
ms.custom: SEO-VS-2020
ms.date: 12/17/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 024926123e8a9967947d11635558eb6ea06077cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921668"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Procedimiento Establecer un nombre de subproceso en código nativo
La denominación de los subprocesos es posible en cualquier edición de Visual Studio. La denominación de los subprocesos es útil para identificar subprocesos de interés en la ventana **Subprocesos** al depurar un proceso en ejecución. El uso de subprocesos con nombre reconocible también puede ser útil cuando se realiza la depuración final a través de la inspección de volcado de memoria y se analizan las capturas de rendimiento mediante diversas herramientas.

## <a name="ways-to-set-a-thread-name"></a>Formas de establecer un nombre de subproceso

Hay dos maneras de establecer el nombre de un subproceso. La primera es a través de la función [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription). La segunda es iniciando una excepción determinada mientras el depurador de Visual Studio está asociado al proceso. Cada enfoque tiene ventajas y advertencias. El uso de `SetThreadDescription` se admite a partir de Windows 10, versión 1607, o Windows Server 2016.

Cabe mencionar que _ambos_ enfoques se pueden usar juntos, si se quiere, porque los mecanismos con los que funcionan son independientes entre sí.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Establecimiento de un nombre de subproceso mediante `SetThreadDescription`

Ventajas:
* Los nombres de los subprocesos son visibles al realizar la depuración en Visual Studio, independientemente de si el depurador estaba asociado o no al proceso en el momento de invocar SetThreadDescription.
* Los nombres de subprocesos son visibles al realizar la depuración final si se carga un volcado de memoria en Visual Studio.
* Los nombres de subprocesos también son visibles al usar otras herramientas, como el depurador [WinDbg](/windows-hardware/drivers/debugger/debugger-download-tools) y el analizador de rendimiento de [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer).

Advertencias:
* Los nombres de subprocesos solo son visibles en la versión 15.6 de Visual Studio 2017 y versiones posteriores.
* Cuando se realiza la depuración final de un archivo de volcado de memoria, los nombres de subprocesos solo son visibles si el bloqueo se creó en la versión 1607 de Windows 10, Windows Server 2016 o versiones posteriores de Windows.

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Establecimiento de un nombre de subproceso mediante el inicio de una excepción

Otra manera de establecer un nombre de subproceso en el programa es comunicar el nombre de subproceso deseado al depurador de Visual Studio mediante el inicio de una excepción configurada de manera especial.

Ventajas:
* Funciona en todas las versiones de Visual Studio.

Advertencias:
* Solo funciona si el depurador está asociado en el momento en que se usa el método basado en excepciones.
* Los nombres de subprocesos establecidos mediante este método no estarán disponibles en herramientas de análisis de rendimiento ni volcados de memoria.

*Ejemplo:*

La función `SetThreadName` que se muestra a continuación muestra este enfoque basado en excepciones. Tenga en cuenta que el nombre del subproceso se copiará automáticamente en el subproceso, de modo que se pueda liberar la memoria del parámetro `threadName` una vez completada la llamada `SetThreadName`.

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
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
- [Cómo: Establecer un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md)
