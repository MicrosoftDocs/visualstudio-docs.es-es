---
title: Funciones de enlace de informe | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557790edc774bab9db43830a4f5fc3e21cfc9758
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279453"
---
# <a name="report-hook-functions"></a>Funciones de enlace de informe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una función de enlace de informe, instalada mediante [_CrtSetReportHook](http://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), se llama cada vez [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) genera un informe de depuración. Se puede utilizar, entre otras cosas, para filtrar informes que se concentran en determinados tipos de asignaciones. Una función de enlace de informe debería tener un prototipo como el siguiente:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 El puntero que se pasa a **_CrtSetReportHook** es de tipo **_CRT_REPORT_HOOK**, tal como se define en CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Cuando la biblioteca en tiempo de ejecución llama a la función de enlace, el *nRptType* argumento contiene la categoría del informe (**_CRT_WARN**, **_CRT_ERROR**, o **_CRT _ASSERT**), *szMsg* contiene un puntero a una cadena de mensaje de informe completamente ensamblada y *retVal* especifica si `_CrtDbgReport` deberían continuar la ejecución normal Después de generar el informe o inicie el depurador. (Un *retVal* valor cero continúa la ejecución, el valor 1 inicia el depurador.)  
  
 Si el enlace encarga el mensaje en cuestión por completo, por lo que se requiera ningún informe, debe devolver **TRUE**. Si devuelve **FALSE**, `_CrtDbgReport` informará del mensaje con normalidad.  
  
## <a name="see-also"></a>Vea también  
 [Función de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



