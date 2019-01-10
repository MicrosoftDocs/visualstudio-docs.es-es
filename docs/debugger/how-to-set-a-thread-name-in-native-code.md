---
title: Procedimiento Establecer un nombre de subproceso en código nativo | Microsoft Docs
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: acddd39df0c91aeef5c425ffa67cb234d76d0473
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961359"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Procedimiento Establecer un nombre de subproceso en código nativo
La denominación de los subprocesos es posible en cualquier edición de Visual Studio. La denominación de los subprocesos es útil para hacer el seguimiento en la ventana **Subprocesos**.

## <a name="set-a-thread-name"></a>Establecer un nombre de subproceso

El `SetThreadName` función es útil para establecer y ver los subprocesos si el depurador está asociado a su código en ejecución. A partir de Visual Studio 2017 versión 15.6, puede usar el [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) función para establecer y ver los nombres de subproceso.

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

## <a name="set-a-thread-name-using-setthreadname"></a>Establecer un nombre de subproceso mediante SetThreadName

Para establecer un nombre de subproceso en el programa, también puede usar el `SetThreadName` funcione, como se muestra en el siguiente ejemplo de código. Observe que el nombre de subproceso se copia en el subproceso para poder liberar la memoria del parámetro `threadName` .  Este método usa un enfoque basado en excepciones que solo funciona si el depurador se adjunta en el momento en que se usa el método basado en excepciones. Nombre de un subproceso que establece con este método no estará disponible en los volcados de memoria o las herramientas de análisis de rendimiento.

En el ejemplo de código siguiente se muestra cómo utilizar `SetThreadName`:

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