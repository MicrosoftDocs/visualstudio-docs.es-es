---
title: Funciones de enlace de informe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 97d39a171d812915a1cf3c1c6450c73098067949
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284203"
---
# <a name="report-hook-functions"></a>Funciones de enlace de informe
Una función de enlace de informe, instalada mediante [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), se llama cada vez [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) genera un informe de depuración. Se puede utilizar, entre otras cosas, para filtrar informes que se concentran en determinados tipos de asignaciones. Una función de enlace de informe debería tener un prototipo como el siguiente:  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 El puntero que se pasa a **_CrtSetReportHook** es de tipo **_CRT_REPORT_HOOK**, tal como se define en CRTDBG. H:  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Cuando la biblioteca en tiempo de ejecución llama a la función de enlace, el *nRptType* argumento contiene la categoría del informe (**_CRT_WARN**, **_CRT_ERROR**, o **_CRT _ASSERT**), *szMsg* contiene un puntero a una cadena de mensaje de informe completamente ensamblada y *retVal* especifica si `_CrtDbgReport` deberían continuar la ejecución normal Después de generar el informe o inicie el depurador. (Un *retVal* valor cero continúa la ejecución, el valor 1 inicia el depurador.)  
  
 Si el enlace encarga el mensaje en cuestión por completo, por lo que se requiera ningún informe, debe devolver **TRUE**. Si devuelve **FALSE**, `_CrtDbgReport` informará del mensaje con normalidad.  
  
## <a name="see-also"></a>Vea también  
 [Función de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
