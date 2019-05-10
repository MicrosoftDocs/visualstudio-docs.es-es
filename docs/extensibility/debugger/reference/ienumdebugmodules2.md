---
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 548bcd0328f7bdf52e47eb9a4295168ca47a2517
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226693"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Esta interfaz enumera una lista de módulos.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar una lista de los módulos cargados para un programa.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Llamadas visuales Studio [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IEnumDebugModules2`.

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera un número especificado de módulos en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Omite un número especificado de módulos en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Obtiene el número de módulos.|

## <a name="remarks"></a>Comentarios
 Visual Studio usa esta interfaz principalmente para actualizar el **módulos** ventana.

 Para los fines de depuración en Visual Studio, un programa es una secuencia lógica de instrucciones de código que pueden cruzar los límites del módulo, por lo tanto, la necesidad de una lista de módulos para una sola [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz. Normalmente, el primer módulo en la lista contiene el punto de entrada inicial para el programa asociado.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)