---
title: "IDebugApplication::QueryCurrentThreadIsDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.QueryCurrentThreadIsDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::QueryCurrentThreadIsDebuggerThread"
ms.assetid: e22ad8a4-a8be-423d-80f2-28256a7448ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::QueryCurrentThreadIsDebuggerThread
Determina si el subproceso actual de ejecución es el subproceso del depurador.  
  
## Sintaxis  
  
```  
HRESULT QueryCurrentThreadIsDebuggerThread();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente y el subproceso actual de ejecución es el subproceso del depurador.|  
|`S_FALSE`|El subproceso actual de ejecución no es el subproceso del depurador.|  
  
## Comentarios  
 Este método determina si el subproceso actual de ejecución es el subproceso del depurador.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)