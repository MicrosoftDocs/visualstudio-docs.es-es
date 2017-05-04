---
title: "IJsDebugFrame::Evaluate (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::Evaluate (M&#233;todo)
Evaluar una expresión en el contexto de este marco de pila.  
  
## Sintaxis  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### Parámetros  
 `pExpressionText`  
 \[in\] Expresión que se va a evaluar.  
  
 `ppDebugProperty`  
 \[out\] Objeto que representa el explorador de propiedades.  
  
 `pError`  
 \[out\] Mensaje de error, si se produce un error.  
  
## Valor devuelto  
  
## Comentarios  
 Devuelve lo siguiente: S\_OK: la evaluación es correcta, \*ppDebugProperty contiene el resultado de la evaluación.  S\_FALSE: La evaluación produce un error \(o no se admite la operación de evaluación\), \*pError contiene el mensaje de error.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugFrame \(Interfaz\)](../../winscript/reference/ijsdebugframe-interface.md)