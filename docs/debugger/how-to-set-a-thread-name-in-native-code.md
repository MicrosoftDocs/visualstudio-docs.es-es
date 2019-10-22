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
ms.openlocfilehash: a89dce28f33bef0ffdb13d6254b2ac6b86ac25db
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589032"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Cómo: Establecer un nombre de subproceso en código nativo
La denominación de los subprocesos es posible en cualquier edición de Visual Studio. La denominación de los subprocesos resulta útil para identificar los subprocesos de interés en la ventana **subprocesos** al depurar un proceso en ejecución. El uso de subprocesos con nombre reconocible también puede ser útil cuando se realiza la depuración posterior a través de la inspección de volcado de memoria y se analizan las capturas de rendimiento mediante diversas herramientas.

## <a name="ways-to-set-a-thread-name"></a>Formas de establecer un nombre de subproceso

Hay dos maneras de establecer un nombre de subproceso. La primera es a través de la función [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) . La segunda es iniciando una excepción determinada mientras el depurador de Visual Studio está asociado al proceso. Cada enfoque tiene ventajas y advertencias. El uso de `SetThreadDescription` se admite a partir de Windows 10, versión 1607 o Windows Server 2016.

Merece la pena mencionar que _ambos_ enfoques se pueden usar juntos, si lo desea, ya que los mecanismos por los que trabajan son independientes entre sí.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Establecer un nombre de subproceso mediante `SetThreadDescription`

Ventajas:
* Los nombres de subprocesos son visibles al depurar en Visual Studio, independientemente de si el depurador se ha asociado al proceso en el momento en que se invoca SetThreadDescription.
* Los nombres de subprocesos están visibles cuando se realiza la depuración posterior mediante la carga de un volcado de memoria en Visual Studio.
* Los nombres de subprocesos también son visibles al usar otras herramientas, como el depurador [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) y el analizador de rendimiento de [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) .

Advertencias:
* Los nombres de subproceso solo están visibles en la versión 15,6 de Visual Studio 2017 y versiones posteriores.
* Cuando se depura después de un archivo de volcado de memoria, los nombres de los subprocesos solo están visibles si el bloqueo se ha creado en la versión 1607 de Windows 10, Windows Server 2016 o versiones posteriores de Windows.

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

Otra manera de establecer un nombre de subproceso en el programa es comunicar el nombre de subproceso deseado al depurador de Visual Studio mediante la generación de una excepción configurada de forma especial.

Ventajas:
* Funciona en todas las versiones de Visual Studio.

Advertencias:
* Solo funciona si el depurador está asociado en el momento en que se utiliza el método basado en excepciones.
* Los nombres de subprocesos establecidos mediante este método no estarán disponibles en volcados de memoria o herramientas de análisis de rendimiento.

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
