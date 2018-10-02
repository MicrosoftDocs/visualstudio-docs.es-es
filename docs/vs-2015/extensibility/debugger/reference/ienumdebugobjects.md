---
title: IEnumDebugObjects | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fdb43790d10ffac3fe081369976fe6ee27e0786
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582956"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IEnumDebugObjects](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugobjects).  
  
> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
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
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Restablece la enumeración a la primera entrada.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera una copia de la enumeración actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera el número de entradas de la enumeración.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz permite que un motor de depuración enumerar a través de un conjunto de objetos en una matriz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)

