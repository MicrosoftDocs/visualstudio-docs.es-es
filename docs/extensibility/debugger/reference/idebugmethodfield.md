---
title: IDebugMethodField | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b42f37e0418ec354b522da102adaff3653cfc6a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Esta interfaz describe un método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa el [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaz. Esta interfaz es una especialización que presenta un método.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz desde el [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaz si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_METHOD`. Además, los métodos, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), y [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), devuelven el `IDebugMethodField` interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) y [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Crea un enumerador para los parámetros del método.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Obtiene el puntero "this" del objeto que contiene el método.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Crea un enumerador para todas las variables locales del método.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Crea un enumerador para seleccionado variables locales del método.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Determina si se ha definido un atributo personalizado específico.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Crea un enumerador para las variables locales estáticas del método.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Obtiene el contenedor global del método.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Crea un enumerador para el tipo de cada argumento que se debe llamar al método.|  
  
## <a name="remarks"></a>Comentarios  
 Un método puede contener parámetros, así como las variables locales.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)