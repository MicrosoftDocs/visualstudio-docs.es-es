---
title: "IEnumDebugFields | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields"
helpviewer_keywords: 
  - "Interfaz IEnumDebugFields"
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa una colección de objetos que implementan la interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Sintaxis  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz está implementada por el proveedor de token para que los conjuntos de objetos que implementan la interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  Observe que esto no es una enumeración COM estándar debido a la presencia del método de [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) .  
  
## Notas para los llamadores  
 esta interfaz es devuelta por [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) y [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## métodos en el orden de Vtable  
 esta interfaz implementa los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera el conjunto de objetos de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Omite un número especificado de entradas.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|restablece la enumeración a la primera entrada.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|recupera una copia de la enumeración actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera el número de entradas de la enumeración.|  
  
## Comentarios  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)