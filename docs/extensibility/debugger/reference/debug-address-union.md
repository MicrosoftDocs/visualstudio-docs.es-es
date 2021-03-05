---
description: Describe distintos tipos de direcciones.
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea2999e85c721ce2582a781b8914241076470710
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170710"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Describe distintos tipos de direcciones.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Members
`dwKind`\
Un valor de la enumeración [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , que especifica cómo interpretar la Unión.

`addr.addrNative`\
[Solo C++] Contiene la estructura de [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) si `dwKind` = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Solo C++] Contiene la estructura de[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) si `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Solo C++] Contiene la estructura de[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) si `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Solo C++] Contiene la estructura de[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) si `dwKind` = ADDRESS_KIND_METHOD.

`addr.addrField`\
[Solo C++] Contiene la estructura de[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) si `dwKind` = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Solo C++] Contiene la estructura de[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) si `dwKind` = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Solo C++] Contiene la estructura de[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) si `dwKind` = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Solo C++] Contiene la estructura de[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) si `dwKind` = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Solo C++] Contiene la estructura de[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) si `dwKind` = ADDRESS_KIND_RETVAL.

`addr.unused`\
[Solo C++] relleno.

`addr`\
[Solo C++] Nombre de la Unión.

`unionmember`\
[Solo C#] Se deben calcular las referencias de este valor en el tipo de estructura apropiado basado en `dwKind` . Vea la sección Comentarios para la asociación entre `dwKind` y la interpretación de la Unión.

## <a name="remarks"></a>Observaciones
Esta estructura forma parte de la estructura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) y representa una serie de diferentes tipos de direcciones (la `DEBUG_ADDRESS` estructura se rellena mediante una llamada al método [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) ).

 [Solo C#] En la tabla siguiente se muestra cómo interpretar el `unionmember` miembro para cada clase de dirección. En el ejemplo se muestra cómo hacerlo para un tipo de dirección.

|`dwKind`|`unionmember` se interpreta como|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo interpretar un tipo de dirección ( `METADATA_ADDRESS_ARRAYELEM` ) de la `DEBUG_ADDRESS_UNION` estructura en C#. Los elementos restantes se pueden interpretar exactamente de la misma manera.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
Encabezado: SH. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
