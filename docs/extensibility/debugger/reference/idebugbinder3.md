---
description: Esta interfaz proporciona acceso a los tipos, alias y servicios del visualizador personalizado.
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f6be3b149450ec84158acc533230102fce5a67e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143615"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz proporciona acceso a los tipos, alias y servicios del visualizador personalizado.

## <a name="syntax"></a>Syntax

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un motor de depuración implementa esta interfaz para admitir los alias, los servicios del visualizador personalizado y el acceso a la información de tipo de objeto.

## <a name="notes-for-callers"></a>Notas para llamadores
 Una interfaz [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obtiene esta interfaz mediante [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Además de los métodos proporcionados por la interfaz [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , esta interfaz implementa lo siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Recupera un objeto de memoria que representa la memoria a la que está enlazado este objeto.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Recupera la excepción asociada a este objeto (si existe).|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Recupera un alias dado su nombre.|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Recupera una matriz de todos los alias de este objeto,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Obtiene el número de tipos de argumento asociado a este objeto.|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Recupera una lista de tipos de argumento asociados a este objeto.|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtiene una interfaz a un servicio del visualizador.|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Convierte una ubicación de objeto o una dirección de memoria de 64 bits en un contexto de memoria.|

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
