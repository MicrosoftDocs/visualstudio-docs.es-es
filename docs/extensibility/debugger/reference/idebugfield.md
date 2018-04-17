---
title: IDebugField | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2ff92f339568a6a20e2f85a0b2deae9c8db244f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfield"></a>IDebugField
Esta interfaz representa un campo, es decir, una descripción de un símbolo o el tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de símbolos implementa esta interfaz como la clase base para todos los campos.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz es la clase base para todos los campos. En función del valor devuelto de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), esta interfaz puede devolver más especializados interfaces mediante [QueryInterface](/cpp/atl/queryinterface). Además, muchas interfaces devuelven `IDebugField` objetos desde diversos métodos.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugField`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtiene pueda mostrar información sobre el tipo o el símbolo.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtiene el tipo de campo.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtiene el tipo de campo.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtiene el contenedor del campo.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtiene la dirección del campo.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtiene el tamaño de un campo, en bytes.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtiene información adicional sobre un campo.|  
|[Igual a](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compara dos campos.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtiene información de independiente del tipo sobre el tipo o símbolo.|  
  
## <a name="remarks"></a>Comentarios  
 Un tipo es equivalente a un lenguaje C `typedef`.  
  
 En el siguiente ejemplo de lenguaje C++ `weather` es un tipo de clase, y `sunny` y `stormy` son símbolos:  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Si un campo representa un símbolo o el tipo se puede determinar mediante una llamada a [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) y examinando la [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) resultado. Si el `FIELD_KIND_TYPE` bit se establece, el campo es un tipo y si el `FIELD_KIND_SYMBOL` bit se establece, se trata de un símbolo.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)