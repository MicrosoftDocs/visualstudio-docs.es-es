---
title: "Funciones de enlace con los bloques de tipo cliente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "_CrtSetDumpClient (función)"
  - "bloques cliente, funciones de enlace"
  - "bloques cliente, validar y notificar datos"
  - "depurar [C++], funciones de enlace"
  - "enlaces, bloque cliente"
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funciones de enlace con los bloques de tipo cliente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si desea validar o informar del contenido de los datos almacenados en bloques `_CLIENT_BLOCK`, puede escribir una función específicamente para ello.  Esta función debe tener un prototipo similar al siguiente, como se define en CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 En otras palabras, la función de enlace debería aceptar un puntero **void** al inicio del bloque de asignación, junto con un valor de tipo **size\_t** que indique el tamaño de la asignación y devuelva `void`.  Aparte de eso, el contenido se puede elegir libremente.  
  
 Una vez instalada la función de enlace mediante [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient), recibirá una llamada cada vez que se realice un volcado de un bloque `_CLIENT_BLOCK`.  Se puede, entonces, utilizar [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) para obtener información del tipo o subtipo de los bloques volcados.  
  
 El puntero a la función que se pasó a `_CrtSetDumpClient` es del tipo **\_CRT\_DUMP\_CLIENT**, según se define en CRTDBG.H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/es-es/21e1346a-6a17-4f57-b275-c76813089167)   
 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)