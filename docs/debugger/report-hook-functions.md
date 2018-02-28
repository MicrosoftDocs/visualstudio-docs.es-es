---
title: Funciones de enlace de informe | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 958c33c623830af509185b3d35ef8a8b5956aaae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="report-hook-functions"></a>Funciones de enlace de informe
Una función de enlace de informe, instalada mediante [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), se llama cada vez que [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) genera un informe de depuración. Se puede utilizar, entre otras cosas, para filtrar informes que se concentran en determinados tipos de asignaciones. Una función de enlace de informe debería tener un prototipo como el siguiente:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 El puntero que se pasa a **_CrtSetReportHook** es de tipo **_CRT_REPORT_HOOK**, tal como se define en CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Cuando la biblioteca en tiempo de ejecución llama a la función de enlace, el *nRptType* argumento contiene la categoría del informe (**_CRT_WARN**, **_CRT_ERROR**, o **_CRT _ASSERT**), *szMsg* contiene un puntero a una cadena de mensaje de informe completamente ensamblada y *retVal* especifica si `_CrtDbgReport` deberían continuar la ejecución normal Después de generar el informe o inicie el depurador. (Un *retVal* valor cero continúa la ejecución, un valor 1 inicia el depurador.)  
  
 Si el enlace encarga el mensaje en cuestión por completo, por lo que no se requiera ningún informe posterior, debería devolver **TRUE**. Si devuelve **FALSE**, `_CrtDbgReport` informará del mensaje normalmente.  
  
## <a name="see-also"></a>Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)