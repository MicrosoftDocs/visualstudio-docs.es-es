---
title: "IDebugExpression::GetResultAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsString"
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsString
Devuelve el resultado de la evaluación de la expresión como una cadena y el valor devuelto de la operación.  
  
## Sintaxis  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### Parámetros  
 `phrResult`  
 \[out\] el valor devuelto de la operación de El.  
  
 `pbstrResult`  
 \[out\] resultado de la evaluación de la expresión.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_PENDING`|La operación todavía está pendiente.|  
  
## Comentarios  
 Este método devuelve el resultado de la evaluación de la expresión como una cadena y `HRESULT`de la operación.  
  
 Este método devuelve `S_OK` y `phrResult` devuelve `E_ABORT` si `Abort` anula la operación.  
  
## Vea también  
 [IDebugExpression \(Interfaz\)](../../winscript/reference/idebugexpression-interface.md)