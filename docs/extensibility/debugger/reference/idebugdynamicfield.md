---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6cd81f393b81adb37059106e2d56fd4a3bf2c461
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921169"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Esta interfaz representa un tipo de una variable.

## <a name="syntax"></a>Sintaxis

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz la implementan los proveedores de símbolos como una clase base para cualquier tipo que se pueda determinar en tiempo de ejecución. Esto es solo para código administrado.

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz representa una clase base de la que se pueden derivar interfaces más especializadas.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Esta interfaz no proporciona ningún método que no sea el heredado de `IDebugField` .

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
