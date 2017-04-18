---
title: IDebugField | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: b96de879e880fc786f3bcedbe797cb66e68e04b9
ms.lasthandoff: 04/05/2017

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
  
```cpp#  
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
