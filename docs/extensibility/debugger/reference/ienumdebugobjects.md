---
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 652d9ad71b780a1ebc3ada8b338e9b2781a50ef6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416072"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz representa una colección de objetos que implementan la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones implementa esta interfaz para proporcionar conjuntos de objetos que implementan la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz. Tenga en cuenta que esto no es una enumeración de COM estándar debido a la presencia de la [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) método.

## <a name="notes-for-callers"></a>Notas para los llamadores
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) devuelve esta interfaz.

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
 Header: ee.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)