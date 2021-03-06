---
description: Esta interfaz representa una colección de objetos que implementan la interfaz IDebugObject.
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eece06d64a4eeefefe4e132295f20e40a032434b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224634"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz representa una colección de objetos que implementan la interfaz [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="syntax"></a>Sintaxis

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones implementa esta interfaz para proporcionar conjuntos de objetos que implementan la interfaz [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) . Tenga en cuenta que esto no es una enumeración COM estándar debido a la presencia del método [getCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) devuelve esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Esta interfaz implementa los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera el siguiente conjunto de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de la enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Omite un número especificado de entradas.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Restablece la enumeración a la primera entrada.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera una copia de la enumeración actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera el número de entradas de la enumeración.|

## <a name="remarks"></a>Observaciones
 Esta interfaz permite a un motor de depuración enumerar en un conjunto de objetos de una matriz.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
