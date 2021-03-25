---
description: Esta interfaz enumera una lista de módulos.
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96a35f11346b769a4329b1212a8202e5e5ded006
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058175"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Esta interfaz enumera una lista de módulos.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) implementa esta interfaz para representar una lista de módulos cargados para un programa.

## <a name="notes-for-callers"></a>Notas para llamadores
 Visual Studio llama a [EnumModules (](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IEnumDebugModules2` .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera un número especificado de módulos en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Omite un número especificado de módulos en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Obtiene el número de módulos.|

## <a name="remarks"></a>Observaciones
 Visual Studio usa esta interfaz principalmente para actualizar la ventana **módulos** .

 En lo que respecta a la depuración en Visual Studio, un programa es una secuencia lógica de instrucciones de código que puede cruzar los límites del módulo, por lo tanto, la necesidad de una lista de módulos para una sola interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . El primer módulo de la lista contiene normalmente el punto de entrada inicial para el programa asociado.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
