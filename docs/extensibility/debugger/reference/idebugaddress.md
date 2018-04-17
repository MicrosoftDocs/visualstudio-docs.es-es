---
title: IDebugAddress | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ace2892d4518de8c5a4abaa2c113df914f9fa6b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugaddress"></a>IDebugAddress
Esta interfaz representa la dirección de un elemento. Se devuelve el controlador de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de símbolos implementa esta interfaz para representar una dirección de un objeto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Muchos métodos de las interfaces devuelven esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura que describe un objeto y su ubicación.|  
  
## <a name="remarks"></a>Comentarios  
 El proveedor de símbolos devuelve esta interfaz para representar un objeto y su ubicación dentro de un ámbito determinado (por ejemplo, función, método o clase). Esta interfaz es devuelto desde y pasa a diversos métodos para el proveedor de símbolos y la expresión evaluador. Normalmente, el proveedor de símbolos es la única entidad que se debe interpretar el contenido de esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)