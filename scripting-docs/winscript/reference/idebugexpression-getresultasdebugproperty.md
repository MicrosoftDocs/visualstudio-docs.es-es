---
title: "IDebugExpression::GetResultAsDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsDebugProperty
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsDebugProperty"
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsDebugProperty
Devuelve el resultado de la evaluación de la expresión como una propiedad de depuración y el valor devuelto de la operación.  
  
## Sintaxis  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### Parámetros  
 `phrResult`  
 \[out\] el valor devuelto de la operación de El.  
  
 `ppdp`  
 \[out\] propiedad de depuración para obtener la expresión.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_PENDING`|La operación todavía está pendiente.|  
  
## Comentarios  
 Este método devuelve el resultado de la evaluación de la expresión como `IDebugProperty` y `HRESULT`de la operación.  
  
 Este método devuelve `S_OK` y `phrResult` devuelve `E_ABORT` si `Abort` anula la operación.  
  
## Vea también  
 [IDebugExpression \(Interfaz\)](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)