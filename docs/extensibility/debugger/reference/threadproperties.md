---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2eb7abf897cf4891f08228dd5f0c918f580a1ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850666"
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

## <a name="members"></a>Members
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

## <a name="remarks"></a>Notas
 Esta estructura se rellena mediante una llamada al método [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . La información que se devuelve se suele usar para rellenar la ventana **subprocesos** .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
