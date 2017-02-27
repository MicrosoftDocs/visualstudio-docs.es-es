---
title: "IEnumDebugAddresses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses"
helpviewer_keywords: 
  - "Interfaz IEnumDebugAddresses"
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa una colección de objetos que implementan la interfaz de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## Sintaxis  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz está implementada por el proveedor de token para que los conjuntos de objetos que implementan la interfaz de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  Observe que esto no es una enumeración COM estándar debido a la presencia del método de [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) .  
  
## Notas para los llamadores  
 esta interfaz es devuelta por [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) y [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## métodos en el orden de Vtable  
 esta interfaz implementa los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera el conjunto de objetos de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Omite un número especificado de entradas.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|restablece la enumeración a la primera entrada.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|recupera una copia de la enumeración actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera el número de entradas de la enumeración.|  
  
## Comentarios  
 Esta interfaz se utiliza normalmente por el motor de depuración para ayudar a determinar la dirección adecuada del evaluador de expresiones.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)