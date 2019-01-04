---
title: IDebugAddress | Documentos de Microsoft
ms.date: 11/04/2016
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
ms.openlocfilehash: bf8c262aef3b562f43409f6d62fc533e4d6314ae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933507"
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
 Muchos métodos en muchas interfaces devuelven esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura que describe un objeto y su ubicación.|  
  
## <a name="remarks"></a>Comentarios  
 El proveedor de símbolos devuelve esta interfaz para representar un objeto y su ubicación dentro de un ámbito determinado (por ejemplo, función, método o clase). Esta interfaz se devuelve desde y pasada a métodos distintos de la expresión y el proveedor de símbolos evaluador. Normalmente, el proveedor de símbolos es la única entidad que se debe interpretar el contenido de esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)