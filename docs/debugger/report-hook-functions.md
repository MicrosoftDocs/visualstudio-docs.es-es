---
title: "Funciones de enlace de informe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtDbgReport (función)"
  - "_CrtSetReportHook (función)"
  - "depurador, funciones de enlace de informe"
  - "depurar [C++], funciones de enlace"
  - "enlaces, informe"
  - "asignación de memoria, montón de depuración"
  - "funciones de enlace de informe"
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Funciones de enlace de informe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una función de enlace de informe, instalada mediante [\_CrtSetReportHook](/visual-cpp/c-runtime-library/reference/crtsetreporthook), recibe una llamada cada vez que [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) genera un informe de depuración.  Se puede utilizar, entre otras cosas, para filtrar informes que se concentran en determinados tipos de asignaciones.  Una función de enlace de informe debería tener un prototipo como el siguiente:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 El puntero que se pasa a **\_CrtSetReportHook** es del tipo **\_CRT\_REPORT\_HOOK**, según se define en CRTDBG.H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Cuando la biblioteca en tiempo de ejecución llama a la función de enlace, el argumento *nRptType* contiene la categoría del informe \(**\_CRT\_WARN**, **\_CRT\_ERROR**, o **\_CRT\_ASSERT**\), *szMsg* contiene un puntero a una cadena de mensaje de informe completamente ensamblada y *retVal* especifica si `_CrtDbgReport` debería continuar con la ejecución normal después de generar el informe o bien iniciar el depurador. Un valor cero en *retVal* permite continuar la ejecución, un valor 1 inicia el depurador.  
  
 Si el enlace se encarga de procesar completamente el mensaje en cuestión, de forma que no se requiera ningún informe posterior, debería devolver **TRUE**.  Si devuelve **FALSE**, `_CrtDbgReport` informará del mensaje como es habitual.  
  
## Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/es-es/21e1346a-6a17-4f57-b275-c76813089167)