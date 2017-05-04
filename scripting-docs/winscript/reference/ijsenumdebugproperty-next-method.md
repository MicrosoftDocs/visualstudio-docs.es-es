---
title: "IJsEnumDebugProperty::Next (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsEnumDebugProperty.Next
apilocation: jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsEnumDebugProperty::Next (M&#233;todo)
Lee propiedades para este objeto.  
  
## Sintaxis  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### Parámetros  
 `count`  
 \[in\] El número de propiedades para leer.  
  
 `ppDebugProperty`  
 \[out\] Objeto que representa el explorador de propiedades.  
  
 `pActualCount`  
 \[out\] Número real de propiedades del objeto.  
  
## Valor devuelto  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsEnumDebugProperty \(Interfaz\)](../../winscript/reference/ijsenumdebugproperty-interface.md)