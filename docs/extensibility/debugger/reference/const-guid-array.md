---
title: CONST_GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40511cac0a6d731d451d1fb2e0e4c02d214297f7
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318542"
---
# <a name="constguidarray"></a>CONST_GUID_ARRAY
Una estructura que contiene una lista de `GUID`s.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagCONST_GUID_ARRAY {
    DWORD       dwCount;
    CONST GUID* Members;
} CONST_GUID_ARRAY;
```

```csharp
public struct CONST_GUID_ARRAY {
    public uint   dwCount;
    public Guid[] Members;
}
```

## <a name="members"></a>Miembros
dwCount  
Número de `GUID`s en el `Members` matriz.

Miembros  
Matriz de `GUID`s.

## <a name="remarks"></a>Comentarios
Esta estructura se pasa a la [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) método y se devuelve desde el [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) y [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) métodos.

El propietario de una instancia de esta estructura es responsable de liberar memoria asignada.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
[Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)  
[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)  
[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)  
[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
