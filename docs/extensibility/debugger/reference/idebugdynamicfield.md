---
title: IDebugDynamicField ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731318"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Esta interfaz representa un tipo de variable.

## <a name="syntax"></a>Sintaxis

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa por los proveedores de símbolos como una clase base para cualquier tipo que se puede determinar en tiempo de ejecución. Esto es solo para código administrado.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Esta interfaz representa una clase base de la que se pueden derivar interfaces más especializadas.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable
 Esta interfaz no proporciona ningún método `IDebugField`distinto de los heredados de .

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
