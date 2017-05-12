---
title: "IActiveScriptErrorDebug::GetStackFrame | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptErrorDebug.GetStackFrame
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptErrorDebug::GetStackFrame"
ms.assetid: a6f43102-68c5-46f5-a4df-fa3aaf53a967
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug::GetStackFrame
Proporciona el marco de pila que esté en efecto para los errores del runtime.  
  
## Sintaxis  
  
```  
HRESULT GetStackFrame(  
   IDebugStackFrame**  ppdsf  
);  
```  
  
#### Parámetros  
 `ppdsf`  
 \[out\] marco de pila para obtener el error.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método proporciona el marco de pila que esté en efecto para los errores en tiempo de ejecución.  
  
## Vea también  
 [IActiveScriptErrorDebug \(Interfaz\)](../../winscript/reference/iactivescripterrordebug-interface.md)