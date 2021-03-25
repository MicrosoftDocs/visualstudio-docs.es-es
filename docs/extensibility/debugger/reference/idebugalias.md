---
description: Representa un alias numérico para una variable.
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5eb9f1d4bc493779d9b42a984c8fc1577e2fe66
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059150"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa un alias numérico para una variable. Un alias es simplemente un nombre diferente para una variable.

## <a name="syntax"></a>Sintaxis

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones (EE) implementa esta interfaz para admitir alias numéricos para variables.

## <a name="notes-for-callers"></a>Notas para llamadores
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) crea un alias para un objeto determinado. Para buscar alias, use [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) o [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Los métodos siguientes se definen en la `IDebugAlias` interfaz.

|Método|Descripción|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtiene el objeto al que hace referencia este alias.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Obtiene el nombre de alias.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Recupera una `ICorDebugValue` interfaz que proporciona acceso a la información de código administrado sobre este objeto (solo código administrado).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marca este alias como que ya no se usa.|

## <a name="remarks"></a>Observaciones
 Un alias es un número decimal en forma de cadena seguido del carácter #, por ejemplo, 1001 #.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
