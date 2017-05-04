---
title: "IJsDebugBreakPoint::GetDocumentPosition (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.GetDocumentPosition
apilocation: jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::GetDocumentPosition (M&#233;todo)
Devuelve la posición de la instrucción donde se enlazó el punto de interrupción.  
  
## Sintaxis  
  
```  
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### Parámetros  
 `pDocumentId`  
 \[out\] Identificador único para un documento de origen \(puntero a IDebugDocumentText\).  
  
 `pCharacterOffset`  
 \[out\] Desplazamiento de carácter de base cero desde el inicio del script.  
  
 `pStatementCharCount`  
 \[out\] Longitud de la instrucción actual, que comienza en el \*pCharacterOffset, en caracteres.  
  
## Valor devuelto  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugBreakPoint \(Interfaz\)](../../winscript/reference/ijsdebugbreakpoint-interface.md)