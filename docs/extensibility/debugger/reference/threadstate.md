---
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96eb95d39c60952c48e62c0e2e61edefeaa59783
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913345"
---
# <a name="threadstate"></a>THREADSTATE
Especifica el estado del subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="members"></a>Miembros
 THREADSTATE_RUNNING indica que se está ejecutando el subproceso.

 THREADSTATE_STOPPED indica que el subproceso se ha detenido debido a un punto de interrupción.

 THREADSTATE_FRESH indica que el subproceso se ha creado pero todavía no ejecuta código.

 THREADSTATE_DEAD indica que el subproceso está inactivo.

 THREADSTATE_FROZEN indica que el subproceso está inmovilizado (no se puede realizar ninguna ejecución).

## <a name="remarks"></a>Comentarios
 Utilizado para la `dwThreadState` campo de la [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estructura.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)