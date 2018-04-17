---
title: IEnumDebugAddresses | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfed705253a03ec550e7533f7e2ab323b7ead62a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Esta interfaz representa una colección de objetos que implementan la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante el proveedor de símbolos para ofrecer conjuntos de objetos que implementan la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz. Tenga en cuenta que esto no es una enumeración de COM estándar debido a la presencia de la [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) método.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz es devuelto por [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) y [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz implementa los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera el siguiente conjunto de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objetos de la enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Omite un número especificado de entradas.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Restablece la enumeración a la primera entrada.|  
|[clon](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Recupera una copia de la enumeración actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera el número de entradas de la enumeración.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se usa normalmente por el motor de depuración para ayudar a determinar la dirección adecuada para dar al evaluador de expresiones.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)