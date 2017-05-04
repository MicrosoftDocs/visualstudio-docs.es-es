---
title: "ISetNextStatement::CanSetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# ISetNextStatement::CanSetNextStatement
Este método determina si el punto de ejecución, que determina el siguiente fragmento de código que se ejecuta, se puede establecer en la ubicación especificada.  
  
## Sintaxis  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### Parámetros  
 `pStackFrame`  
 \[in\] puntero a un objeto del marco de pila.  
  
 `pCodeContext`  
 \[in\] puntero a un objeto de contexto del código.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El siguiente fragmento se puede actualizar el contexto especificado de código.|  
|`S_FALSE`|El siguiente fragmento no se puede actualizar el contexto especificado de código.|  
  
## Comentarios  
  
## Vea también  
 [ISetNextStatement \(Interfaz\)](../../winscript/reference/isetnextstatement-interface.md)