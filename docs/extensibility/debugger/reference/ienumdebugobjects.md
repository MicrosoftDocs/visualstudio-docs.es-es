---
title: IEnumDebugObjects | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 99c6c7a98074753e9ee7e1364adb35e1cdba9700
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz representa una colección de objetos que implementan la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones implementa esta interfaz para proporcionar conjuntos de objetos que implementan la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz. Tenga en cuenta que esto no es una enumeración de COM estándar debido a la presencia de la [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) método.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) devuelve esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz implementa los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera el siguiente conjunto de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos de la enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Omite un número especificado de entradas.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Restablece la enumeración a la primera entrada.|  
|[clon](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera una copia de la enumeración actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera el número de entradas de la enumeración.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz permite usar un motor de depuración enumerar un conjunto de objetos en una matriz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)