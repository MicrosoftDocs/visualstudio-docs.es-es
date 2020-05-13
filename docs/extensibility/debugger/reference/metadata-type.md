---
title: METADATA_TYPE de la casa de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714283"
---
# <a name="metadata_type"></a>METADATA_TYPE
Esta estructura especifica información sobre un tipo de campo tomado de metadatos.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parámetros
 `ulAppDomainID`\
 ID de la aplicación de la que procede el símbolo. Esto se utiliza para identificar de forma única una instancia de la aplicación.

 `guidModule`\
 Guid del módulo que contiene este campo.

 `tokClass`\
 El identificador de token de metadatos de este tipo.

 [C++] `_mdToken` es `typedef` un para un `int`32-bit .

## <a name="remarks"></a>Observaciones
 Esta estructura aparece como parte de la `dwKind` unión `TYPE_INFO` en la `TYPE_KIND_METADATA` [estructura TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) cuando se establece el campo de la estructura en (un valor de la [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeración).

 El `tokClass` valor es un token de metadatos que identifica de forma única un tipo. Para obtener más información sobre cómo interpretar los bits `CorTokenType` superiores del identificador de token de metadatos, vea la enumeración en el archivo corhdr.h en el SDK de .NET Framework.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
