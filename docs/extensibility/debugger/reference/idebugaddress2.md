---
title: IDebugAddress2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 588b2d3e338080a086fee421deb17760496a268f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugaddress2"></a>IDebugAddress2
Esta interfaz proporciona acceso al identificador del proceso que posee el objeto cuya dirección está representado por esta interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa el [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz. Esta interfaz proporciona acceso al identificador del proceso que posee el objeto que está relacionado con esta dirección.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz desde el [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de vtable  
 Además de los métodos heredados de la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz, esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera el identificador del proceso que posee el objeto representado por esta interfaz.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)