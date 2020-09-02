---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4bc592ff0198d4cc93d500c39167e214e63f032
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702589"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina la existencia de un atributo personalizado para este campo y, si existe, devuelve la información de atributo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) para admitir atributos personalizados.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Use [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para obtener esta interfaz de la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de la interfaz **IDebugCustomAttributeQuery** .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Determina si un atributo personalizado existe por nombre.|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Obtiene la información de atributo para el atributo personalizado especificado.|  
  
 Además de los métodos **IDebugCustomAttributeQuery** , `IDebugCustomAttributeQuery2` implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Obtiene un enumerador para todos los atributos personalizados asociados a este campo.|  
  
## <a name="remarks"></a>Observaciones  
 El método [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) puede devolver un enumerador para todos los atributos personalizados definidos para este campo.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: SH. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
