---
title: IDebugArrayObject2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc101fa7e0f339a599bd48f1954c0f6ed165f47f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa un objeto de matriz administrada y permite que un evaluador de expresiones (EE) para determinar el índice de base (inferior) de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esto se implementa mediante el motor de depuración administrado (Alemania).  
  
## <a name="methods"></a>Métodos  
 Además de los métodos en el [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) interfaz, esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Recupera los índices de base (inferior) para cada índice dado el número de dimensiones de la matriz.|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Determina si la matriz tiene índices de base (límites inferiores) definidos.|  
  
## <a name="remarks"></a>Comentarios  
 Un evaluador de expresiones utiliza esta interfaz para representar las matrices administradas en un árbol de análisis.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll