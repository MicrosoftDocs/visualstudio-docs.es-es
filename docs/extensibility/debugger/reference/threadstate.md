---
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21b683e8f7797743d5ae78f932edfa5c862dbb8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967688"
---
# <a name="threadstate"></a>THREADSTATE
Especifica el estado del subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Campos
 `THREADSTATE_RUNNING`\
 Indica que el subproceso se está ejecutando.

 `THREADSTATE_STOPPED`\
 Indica que el subproceso se ha detenido debido a un punto de interrupción.

 `THREADSTATE_FRESH`\
 Indica que se ha creado el subproceso, pero que aún no se está ejecutando código.

 `THREADSTATE_DEAD`\
 Indica que el subproceso está inactivo.

 `THREADSTATE_FROZEN`\
 Indica que el subproceso está inmovilizado (no se puede realizar ninguna ejecución).

## <a name="remarks"></a>Notas
 Se usa para el `dwThreadState` campo de la estructura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
