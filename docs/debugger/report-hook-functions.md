---
title: Funciones de enlace de informe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce84105fa1a3d7bf5c6f949421b306b5147368a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892360"
---
# <a name="report-hook-functions"></a>Funciones de enlace de informe
Una función de enlace de informe, instalada mediante [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), recibe una llamada cada vez que [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) genera un informe de depuración. Se puede utilizar, entre otras cosas, para filtrar informes que se concentran en determinados tipos de asignaciones. Una función de enlace de informe debería tener un prototipo como el siguiente:  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 El puntero que se pasa a **_CrtSetReportHook** es de tipo **_CRT_REPORT_HOOK**, tal como se define en CRTDBG. H:  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Cuando la biblioteca en tiempo de ejecución llama a la función de enlace, el argumento *nRptType*contiene la categoría del informe (**_CRT_WARN**, **_CRT_ERROR** o **_CRT_ASSERT**), *szMsg* contiene un puntero a una cadena de mensaje de informe completamente ensamblada y *retVal* especifica si `_CrtDbgReport` debería continuar con la ejecución normal después de generar el informe o bien iniciar el depurador. Un valor cero en *retVal* permite continuar la ejecución, un valor 1 inicia el depurador.  
  
 Si el enlace se encarga de procesar completamente el mensaje en cuestión, de forma que no se requiera ningún informe posterior, debería devolver **TRUE**. Si devuelve **FALSE**, `_CrtDbgReport` informará del mensaje como es habitual.  
  
## <a name="see-also"></a>Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
