---
title: BP_LOCATION Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737933"
---
# <a name="bp_location"></a>BP_LOCATION
Especifica el tipo de estructura utilizado para describir la ubicación del punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Miembros
`bpLocationType`\
Un valor de la [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) `bpLocation` enumeración `unionmemberX` utilizada para interpretar la unión o los miembros.

`bpLocation`.`bplocCodeFileLine`\
[Sólo C++] Contiene [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) la estructura `bpLocationType`  =  `BPLT_CODE_FILE_LINE`BP_LOCATION_CODE_FILE_LINE si .

`bpLocation.bplocCodeFuncOffset`\
[Sólo C++] Contiene [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) la estructura `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`BP_LOCATION_CODE_FUNC_OFFSET si .

`bpLocation.bplocCodeContext`\
[Sólo C++] Contiene [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) la estructura `bpLocationType`  =  `BPLT_CODE_CONTEXT`BP_LOCATION_CODE_CONTEXT si .

`bpLocation.bplocCodeString`\
[Sólo C++] Contiene [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) la estructura `bpLocationType`  =  `BPLT_CODE_STRING`BP_LOCATION_CODE_STRING si .

`bpLocation.bplocCodeAddress`\
[Sólo C++] Contiene la estructura `bpLocationType`  =  `BPLT_CODE_ADDRESS` [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) si .

`bpLocation.bplocDataString`\
[Sólo C++] Contiene [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) la estructura `bpLocationType`  =  `BPLT_DATA_STRING`BP_LOCATION_DATA_STRING si .

`bpLocation.bplocResolution`\
[Sólo C++] Contiene [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) la estructura `bpLocationType`  =  `BPLT_RESOLUTION`BP_LOCATION_RESOLUTION si .

`unionmember1`\
[Sólo C] Consulte Comentarios sobre cómo interpretar.

`unionmember2`\
[Sólo C] Consulte Comentarios sobre cómo interpretar.

`unionmember3`\
[Sólo C] Consulte Comentarios sobre cómo interpretar.

`unionmember4`\
[Sólo C] Consulte Comentarios sobre cómo interpretar.

## <a name="remarks"></a>Observaciones
Esta estructura es un miembro de las estructuras [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

 [Sólo C] Los `unionmemberX` miembros se interpretan de acuerdo con la tabla siguiente. Mire hacia abajo `bpLocationType` la columna izquierda para el valor `unionmemberX` y luego `unionmemberX` mire a través de las otras columnas para determinar lo que representa cada miembro y calcular las referencias de la en consecuencia. Vea el ejemplo para una manera de interpretar una parte de esta estructura en C.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(un contexto)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(un contexto)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(un contexto)|`string`(expresión condicional)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(un contexto)|`string`(URL del módulo)|`string`(nombre de la función)|`string`(dirección)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(un contexto)|`string`(expresión de datos)|`uint`(número de elementos)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Ejemplo
En este ejemplo se `BP_LOCATION` muestra cómo interpretar `BPLT_DATA_STRING` la estructura en C- para el tipo. Este tipo en particular muestra `unionmemberX` cómo interpretar los cuatro miembros en todos los formatos posibles (objeto, cadena y número).

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
