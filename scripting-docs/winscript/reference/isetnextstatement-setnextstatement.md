---
title: "ISetNextStatement::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.SetNextStatement
apilocation: scrobj.dll
ms.assetid: c5534f3b-39a5-4466-b8fc-69b717c6eee9
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ISetNextStatement::SetNextStatement
Este método actualiza el contexto siguiente del código que el intérprete de script puede ejecutar.  
  
## Sintaxis  
  
```  
HRESULT SetNextStatement(  
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
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [ISetNextStatement \(Interfaz\)](../../winscript/reference/isetnextstatement-interface.md)