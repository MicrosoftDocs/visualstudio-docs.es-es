---
title: "IEnumJsStackFrames (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames (Interfaz)
Implementado por el depurador para proporcionar un desenredo de pila a jscript9diag.dll para JavaScript.  
  
## Sintaxis  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## Members  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[IEnumJsStackFrames::Next \(Método\)](../../winscript/reference/ienumjsstackframes-next-method.md)|Obtiene el número especificado de fotogramas.|  
|[IEnumJsStackFrames::Reset \(Método\)](../../winscript/reference/ienumjsstackframes-reset-method.md)|Restablece el marco de pila en la posición anterior al primer elemento.|  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)