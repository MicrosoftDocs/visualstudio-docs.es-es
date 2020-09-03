---
title: METADATA_TYPE | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714283"
---
# <a name="metadata_type"></a>METADATA_TYPE
Esta estructura especifica información sobre un tipo de campo tomado de los metadatos.

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
 IDENTIFICADOR de la aplicación de la que procede el símbolo. Se utiliza para identificar de forma única una instancia de la aplicación.

 `guidModule`\
 GUID del módulo que contiene este campo.

 `tokClass`\
 IDENTIFICADOR del token de metadatos de este tipo.

 [C++] `_mdToken` es un `typedef` para un 32 bits `int` .

## <a name="remarks"></a>Observaciones
 Esta estructura aparece como parte de la Unión en la estructura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) cuando el `dwKind` campo de la `TYPE_INFO` estructura se establece en `TYPE_KIND_METADATA` (un valor de la enumeración [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

 El `tokClass` valor es un token de metadatos que identifica un tipo de forma única. Para obtener más información sobre cómo interpretar los bits superiores del identificador del token de metadatos, consulte la `CorTokenType` enumeración en el archivo CorHdr. h en el SDK de .NET Framework.

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
