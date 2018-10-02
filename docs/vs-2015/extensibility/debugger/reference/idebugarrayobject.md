---
title: IDebugArrayObject | Documentos de Microsoft
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
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02d8c9758dc12a5f19f489d1221446bd4b855c96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581938"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugArrayObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugarrayobject).  
  
> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz representa un objeto de matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones implementa esta interfaz para representar una matriz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz puede obtener esta interfaz mediante [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) si el objeto representa una matriz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el `IDebugObject` interfaz, se implementan los métodos siguientes en el `IDebugArrayObject` interfaz.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Obtiene el número de elementos de la matriz.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Obtiene un elemento de la matriz.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Obtiene todos los elementos de la matriz.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Obtiene el rango de la matriz.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Obtiene las dimensiones de la matriz.|  
  
## <a name="remarks"></a>Comentarios  
 Un evaluador de expresiones utiliza esta interfaz para representar las matrices en un árbol de análisis.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

