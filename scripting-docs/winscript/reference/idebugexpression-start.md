---
title: "IDebugExpression::Start | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.Start
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::Start"
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::Start
Inicia la evaluación de la expresión.  
  
## Sintaxis  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### Parámetros  
 `pdecb`  
 \[in\] Callback para indicar cuando la evaluación de la expresión.  Si este parámetro es `NULL`, no se desencadena ningún evento y el cliente debe sondear el estado de la expresión utilizando `QueryIsComplete`.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método inicia la evaluación de la expresión.  
  
## Vea también  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [IDebugExpression \(Interfaz\)](../../winscript/reference/idebugexpression-interface.md)