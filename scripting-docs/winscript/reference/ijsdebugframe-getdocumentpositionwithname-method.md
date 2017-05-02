---
title: "IJsDebugFrame::GetDocumentPositionWithName (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithName (M&#233;todo)
Devuelve la posición actual de este marco de pila en el documento de usuario.  
  
## Sintaxis  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### Parámetros  
 `pDocumentName`  
 \[out\] Para scripts estáticos, una dirección URL para documentar.  En los scripts dinámicos, se devuelve un nombre que contiene el tipo de script \(por ejemplo, código eval, código de función etc.\).  
  
 `pLine`  
 \[out\] Posición de línea basada en uno dentro del documento.  
  
 `pColumn`  
 \[out\] Posición de línea basada en uno dentro del documento.  
  
## Valor devuelto  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugFrame \(Interfaz\)](../../winscript/reference/ijsdebugframe-interface.md)