---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726076"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz proporciona información adicional sobre un objeto.

## <a name="syntax"></a>Sintaxis

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones implementa esta interfaz para ofrecer compatibilidad con los alias y el acceso a la información sobre el objeto.

## <a name="notes-for-callers"></a>Notas para llamadores
 Una interfaz [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) puede obtener esta interfaz mediante [QueryInterface](/cpp/atl/queryinterface). Además, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) devuelve esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Además de los métodos de la interfaz [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , la `IDebugObject2` interfaz implementa lo siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtiene el campo o la variable (si existe) que puede estar respaldando la propiedad representada por este objeto.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtiene el objeto de código administrado que representa el valor de este objeto.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Crea un identificador único para este objeto o devuelve un alias existente.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtiene el alias asociado a este objeto, si existe.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtiene el tipo de este objeto.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina si este objeto representa datos de usuario.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina si el estado de edición y continuación ya no es válido.<br /><br /> Un evaluador de expresiones personalizado no implementa este método (siempre debe devolver `E_NOTIMPL` ).|

## <a name="remarks"></a>Observaciones
 Consulte [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) para obtener una descripción de los alias.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
