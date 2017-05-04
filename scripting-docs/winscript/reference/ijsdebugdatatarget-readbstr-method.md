---
title: "IJsDebugDataTarget::ReadBSTR (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadBSTR (M&#233;todo)
Lee BSTR del destino de depuración.  
  
## Sintaxis  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### Parámetros  
 `address`  
 \[in\] Dirección de la que leer.  
  
 `pString`  
 \[out\] BSTR leído del destino de depuración.  
  
## Valor devuelto  
  
## Comentarios  
 Devuelve E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS si la dirección no es válida.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugDataTarget \(Interfaz\)](../../winscript/reference/ijsdebugdatatarget-interface.md)