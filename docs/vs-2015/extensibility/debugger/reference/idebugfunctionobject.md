---
title: IDebugFunctionObject | Microsoft Docs
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
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56a0e0c7dffa23698e83214e8a1b4293e68be210
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804025"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz representa una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un evaluador implementa esta interfaz para representar una función.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz es una especialización de la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz y se obtiene mediante [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en el `IDebugObject` interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), el `IDebugFunctionObject` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Crea un objeto de datos primitivos.|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Crea un objeto utilizando un constructor.|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Crea un objeto con ningún constructor.|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Crea un objeto de matriz.|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Crea un objeto de cadena.|  
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Llama a la función y devuelve el valor resultante como un objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz permite que el evaluador de expresiones que representan las funciones en un árbol de análisis. El `Create` los métodos de esta interfaz se utilizan para construir objetos que representan los parámetros de entrada al método. A continuación, se puede ejecutar la función mediante una llamada a la [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) método, que devuelve un objeto que representa el valor devuelto de la función.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

