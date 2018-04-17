---
title: IDebugContainerField | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bee04d21e3181d4590f26b64c794164ab1a84b6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Esta interfaz representa un símbolo o el tipo que es un contenedor para otros símbolos o tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz. Esta interfaz también es la clase base para todas las interfaces que representan contenedores.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Muchos métodos de las interfaces devuelven esta interfaz. Dado que se trata de una clase base para todos los contenedores, puede obtener interfaces más especializadas de esta interfaz mediante [QueryInterface](/cpp/atl/queryinterface). Estas interfaces incluyen [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), y [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz, esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumerador para los campos del contenedor.|  
  
## <a name="remarks"></a>Comentarios  
 Matrices (contenedores para las variables), clases (contenedores para los métodos y variables) y métodos (contenedores para los parámetros y variables locales) son ejemplos de contenedores.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)