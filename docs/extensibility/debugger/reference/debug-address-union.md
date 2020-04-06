---
title: DEBUG_ADDRESS_UNION de la casa de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737529"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Describe diferentes tipos de direcciones.

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

## <a name="members"></a>Miembros
`dwKind`\
Un valor de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeración, especificando cómo interpretar la unión.

`addr.addrNative`\
[Sólo C++] Contiene la estructura `dwKind` de [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) si ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Sólo C++] Contiene la estructura `dwKind` de[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) si ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Sólo C++] Contiene la estructura `dwKind` de[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) si ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Sólo C++] Contiene la estructura `dwKind` de[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) si ADDRESS_KIND_METHOD.

`addr.addrField`\
[Sólo C++] Contiene la estructura `dwKind` de[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) si ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Sólo C++] Contiene la estructura `dwKind` de[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) si ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Sólo C++] Contiene la estructura `dwKind` de[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) si ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Sólo C++] Contiene la estructura `dwKind` de[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) si ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Sólo C++] Contiene la estructura `dwKind` de[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) si ADDRESS_KIND_RETVAL.

`addr.unused`\
Relleno [solo C++].

`addr`\
[Sólo C++] El nombre del sindicato.

`unionmember`\
[Sólo C] Este valor debe calcularse en el tipo `dwKind`de estructura adecuado en función de . Véanse las observaciones `dwKind` para la asociación entre la unión y su interpretación.

## <a name="remarks"></a>Observaciones
Esta estructura forma parte de la [estructura DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) y representa uno `DEBUG_ADDRESS` de varios tipos diferentes de direcciones (la estructura se rellena mediante una llamada a la [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método).

 [Sólo C] En la tabla siguiente `unionmember` se muestra cómo interpretar el miembro para cada tipo de dirección. El ejemplo muestra cómo se hace esto para un tipo de dirección.

|`dwKind`|`unionmember`interpretado como|
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
En este ejemplo se muestra cómo`METADATA_ADDRESS_ARRAYELEM`interpretar `DEBUG_ADDRESS_UNION` un tipo de dirección ( ) de la estructura en C. Los elementos restantes se pueden interpretar exactamente de la misma manera.

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
Encabezado: sh.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
