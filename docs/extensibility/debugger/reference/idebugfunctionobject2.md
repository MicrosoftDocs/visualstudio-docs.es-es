---
title: IDebugFunctionObject2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6b051cc033f41f78fb1f2e6ed18eb22de6f8f0aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa una función y mejora la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un evaluador de expresiones (EE) implementa esta interfaz para representar una función.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Métodos de esta interfaz aplazan los de **IDebugFunctionObject** de las maneras siguientes:  
  
-   El **IDebugEvaluate** método toma marcas.  
  
-   El **CreateObject** método toma marcas y un tiempo de espera.  
  
-   El **CreateStringObjectWithLength** método toma una longitud.  
  
## <a name="methods"></a>Métodos  
 Esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crea un objeto que se utiliza un constructor según los valores de marca de evaluación y un valor de tiempo de espera.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crea un objeto de cadena que tiene la longitud especificada.|  
|[evaluar](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Llama a la función y devuelve el valor resultante como un objeto.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll