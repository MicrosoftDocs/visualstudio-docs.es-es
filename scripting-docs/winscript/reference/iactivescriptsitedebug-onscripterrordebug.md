---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::OnScriptErrorDebug"
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::OnScriptErrorDebug
Permite que un host inteligente determine cómo controlar errores en tiempo de ejecución.  
  
## Sintaxis  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Parámetros  
 `pErrorDebug`  
 \[in\] error en tiempo de ejecución a El que se produjo  
  
 `pfEnterDebugger`  
 \[out\] marca que indica si pasar el error el depurador para realizar la depuración JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 \[out\] marca que indica si llamar `IActiveScriptSite::OnScriptError` cuando el usuario decide continuar sin depurar.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan al valor en la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Un host inteligente puede utilizar este método para determinar cómo administrar los errores en tiempo de ejecución.  
  
## Vea también  
 [IActiveScriptSiteDebug \(Interfaz\)](../../winscript/reference/iactivescriptsitedebug-interface.md)