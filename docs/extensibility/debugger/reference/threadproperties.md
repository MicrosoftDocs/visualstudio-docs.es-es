---
description: Describe las propiedades de un subproceso.
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0707cb5da4c63ffd686f22fa691c103c954478c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070861"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Describe las propiedades de un subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>Miembros
 `dwFields`\
 Combinación de marcas de la enumeración [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , que describe los campos de esta estructura válidos.

 `dwThreadId`\
 IDENTIFICADOR del subproceso.

 `dwSuspendCount`\
 Recuento de suspensiones de subproceso.

 `dwThreadState`\
 Un valor de la enumeración [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) que indica el estado del subproceso operativo.

 `bstrPriority`\
 Cadena que especifica la prioridad del subproceso; por ejemplo, "por encima de lo normal", "normal" o "tiempo crítico".

 `bstName`\
 Nombre del subproceso.

 `bstrLocation`\
 La ubicación del subproceso (normalmente, el marco de pila más alto), normalmente expresada como el nombre del método en el que se detiene la ejecución.

## <a name="remarks"></a>Observaciones
 Esta estructura se rellena mediante una llamada al método [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . La información que se devuelve se suele usar para rellenar la ventana **subprocesos** .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
