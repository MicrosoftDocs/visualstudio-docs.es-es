---
title: "Cómo: establecer un nombre de subproceso en código nativo | Documentos de Microsoft"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ded01065c3971daf630fd743d0ad017e2b3d91c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Cómo: Establecer un nombre de subproceso en código nativo
La denominación de los subprocesos es posible en cualquier edición de Visual Studio. Denominación de los subprocesos es útil para realizar el seguimiento de subprocesos en la **subprocesos** ventana.

Para establecer el nombre de un subproceso en el programa, utilice la función `SetThreadName` , como se muestra en el siguiente ejemplo de código. Observe que el nombre de subproceso se copia en el subproceso para poder liberar la memoria del parámetro `threadName` .  
  
## <a name="example"></a>Ejemplo  
  
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
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Ver los datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Cómo: Establecer un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md)