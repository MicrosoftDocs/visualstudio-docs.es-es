---
title: "IDebugAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress"
helpviewer_keywords: 
  - "Interfaz IDebugAddress"
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa la dirección de un elemento.  Devuelve el controlador de símbolos.  
  
## Sintaxis  
  
```  
IDebugAddress : IUnknown  
```  
  
## Notas para los implementadores  
 Un proveedor de token implementa esta interfaz para representar una dirección de un objeto.  
  
## Notas para los llamadores  
 Muchos métodos en las interfaces devuelven esta interfaz.  
  
## métodos en el orden de Vtable  
 esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|recupera una estructura de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) que describe un objeto y su ubicación.|  
  
## Comentarios  
 El proveedor del token devuelve esta interfaz para representar un objeto y su ubicación dentro de un ámbito determinado \(por ejemplo, función, método, o clase\).  Esta interfaz se devuelve de y se pasa a los diversos métodos del proveedor del token y el evaluador de expresiones.  Normalmente, el proveedor del token es la única entidad que necesita interpretar el contenido de esta interfaz.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)