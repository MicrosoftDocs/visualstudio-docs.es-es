---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e62eefefe0e0a4f28c2ec2efe457017d940aaa2e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649869"
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
Describe los distintos tipos de direcciones.

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

## <a name="terms"></a>Términos
dwKind un valor de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeración, que especifica cómo interpretar la unión.

addr.addrNative

 [C++ sólo] Contiene el [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) estructura si `dwKind` = ADDRESS_KIND_NATIVE.

addr.addrThisRel

 [C++ sólo] Contiene el[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) estructura si `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

addr.addUPhysical

 [C++ sólo] Contiene el[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) estructura si `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.

addr.addrMethod

 [C++ sólo] Contiene el[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) estructura si `dwKind` = ADDRESS_KIND_METHOD.

addr.addrField

 [C++ sólo] Contiene el[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) estructura si `dwKind` = ADDRESS_KIND_FIELD.

addr.addrLocal

 [C++ sólo] Contiene el[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) estructura si `dwKind` = ADDRESS_KIND_LOCAL.

addr.addrParam

 [C++ sólo] Contiene el[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) estructura si `dwKind` = ADDRESS_KIND_PARAM.

addr.addrArrayElem

 [C++ sólo] Contiene el[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) estructura si `dwKind` = ADDRESS_KIND_ARRAYELEM.

addr.addrRetVal

 [C++ sólo] Contiene el[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) estructura si `dwKind` = ADDRESS_KIND_RETVAL.

addr.unused

 [C++ solo] relleno.

addr

 [C++ sólo] El nombre de la unión.

UnionMember

 [C# sólo] Este valor tiene que calcularse para el tipo de estructura adecuada según `dwKind`. Vea la sección Comentarios para la asociación entre `dwKind` y la interpretación de la unión.

## <a name="remarks"></a>Comentarios
Esta estructura es parte de la [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura y representa una cantidad de diferentes tipos de direcciones (el `DEBUG_ADDRESS` estructura se rellena mediante una llamada a la [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método).

 [C# sólo] En la tabla siguiente se muestra cómo interpretar la `unionmember` miembro para cada tipo de dirección. El ejemplo muestra cómo hacerlo para un tipo de dirección.

|`dwKind`|`unionmember` interpreta como|
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
En este ejemplo se muestra cómo interpretar un tipo de dirección (`METADATA_ADDRESS_ARRAYELEM`) de la `DEBUG_ADDRESS_UNION` estructura en C#. Exactamente del mismo modo, se pueden interpretar los elementos restantes.

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

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
