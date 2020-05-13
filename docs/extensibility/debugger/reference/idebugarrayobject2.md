---
title: IDebugArrayObject2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a6580d0cbdead7866bbc6dd106a2aa0ea56f76
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736231"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa un objeto de matriz administrada y permite que un evaluador de expresiones (EE) determine el índice base (límites inferiores) de la matriz.

## <a name="syntax"></a>Sintaxis

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esto lo implementa el motor de depuración administrado (DE).

## <a name="methods"></a>Métodos
 Además de los métodos de la [interfaz IDebugArrayObject,](../../../extensibility/debugger/reference/idebugarrayobject.md) esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Recupera los índices base (límites inferiores) para cada índice dado el número de dimensiones de la matriz.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Determina si la matriz tiene índices base (límites inferiores) definidos.|

## <a name="remarks"></a>Observaciones
 Un evaluador de expresiones utiliza esta interfaz para representar matrices administradas en un árbol de análisis.

## <a name="requirements"></a>Requisitos
 Encabezado: Ee.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
