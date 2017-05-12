---
title: "IDebugExpressionCallBack::onComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionCallBack.onComplete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExpressionCallBack::onComplete"
ms.assetid: d0b89db3-38e7-44e0-93fe-60205f9149dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionCallBack::onComplete
Indica que la evaluación de la expresión está completa.  
  
## Sintaxis  
  
```  
HRESULT onComplete();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Se llama a este método cuando se completa la evaluación de la expresión.  El método de `IDebugExpression::GetResultAsString` se puede llamar dentro de este controlador de eventos.  
  
## Vea también  
 [IDebugExpressionCallBack \(Interfaz\)](../../winscript/reference/idebugexpressioncallback-interface.md)   
 [IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)