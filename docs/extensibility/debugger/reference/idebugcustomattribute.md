---
title: IDebugCustomAttribute | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0d7497f5fcda3b871c5a1ad57cf04767617bdab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107769"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Esta interfaz representa un atributo personalizado, y puede proporcionar el nombre, el elemento primario y el tipo de clase del atributo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de símbolos implementa esta interfaz para admitir atributos personalizados asociados con un símbolo. Normalmente se implementa en su propio objeto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [siguiente](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) devuelve esta interfaz. Una llamada a la [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) método devuelve el [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugCustomAttribute`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Obtiene el campo al que está asociado el atributo actual.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Obtiene el tipo de clase de atributo personalizado.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Obtiene el nombre del atributo personalizado.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Obtiene la información de atributo como un blob de bytes.|  
  
## <a name="remarks"></a>Comentarios  
 Un atributo personalizado es una estructura de C# que proporciona metadatos personalizados asociados a una determinada clase o método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)