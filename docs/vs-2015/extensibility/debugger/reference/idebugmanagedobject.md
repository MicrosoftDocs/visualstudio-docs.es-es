---
title: IDebugManagedObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eff42a7ba1b2fb3850e3751928d07cc3181d6fcd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783901"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz permite que el evaluador de expresiones (EE) para llamar a métodos o propiedades en las instancias de clase de valor (por ejemplo, `System.Decimal`) y establecer su valor sin llamar a [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) en el programa que se está depurando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un evaluador implementa esta interfaz para representar un objeto de código administrado, como una variable.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Para obtener esta interfaz, llame a [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) en un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa una instancia de una clase de valor.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), el `IDebugManagedObject` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Devuelve una interfaz que representa el objeto de código administrado y de que cualquier código administrado adecuado se puede obtener la interfaz.|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Establece el valor de este objeto en el valor de un objeto de código administrado especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Un evaluador de expresiones utiliza esta interfaz para almacenar un objeto de código administrado en un árbol de análisis.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)

