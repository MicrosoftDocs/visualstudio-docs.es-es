---
description: Especifica la estructura de la ubicación de resolución del punto de interrupción.
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87fef44d02911e84952f6eb8ab09dd9a1360dea6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162568"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Especifica la estructura de la ubicación de resolución del punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Members
`bpType`\
Un valor de la enumeración [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) que especifica cómo interpretar la `bpResLocation` Unión o `unionmemberX` los miembros.

`bpResLocation.bpresCode`\
[Solo C++] Contiene la estructura de [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) si `bpType`  =  `BPT_CODE` .

`bpResLocation.bpresData`\
[Solo C++] Contiene la estructura de [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) si `bpType`  =  `BPT_DATA` .

`bpResLocation.unused`\
[Solo C++] Marcador de posición.

`unionmember1`\
[Solo C#] Vea los comentarios sobre cómo interpretar.

`unionmember2`\
[Solo C#] Vea los comentarios sobre cómo interpretar.

`unionmember3`\
[Solo C#] Vea los comentarios sobre cómo interpretar.

`unionmember4`\
[Solo C#] Vea los comentarios sobre cómo interpretar.

## <a name="remarks"></a>Observaciones
Esta estructura es miembro de las estructuras [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) y [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .

 [Solo C#] Los `unionmemberX` miembros se interpretan según la tabla siguiente. Busque en la columna izquierda el `bpType` valor que se muestra a continuación para determinar lo que `unionmemberX` representa cada miembro y calcular las referencias en `unionmemberX` consecuencia. Vea el ejemplo para obtener una manera de interpretar esta estructura en C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (expresión de datos)|`string` (nombre de función)|`string` (nombre de la imagen)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo interpretar la `BP_RESOLUTION_LOCATION` estructura en C#.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
