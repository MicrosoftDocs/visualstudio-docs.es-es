---
title: PDB_TYPE de la casa de la casa de Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714105"
---
# <a name="pdb_type"></a>PDB_TYPE

Esta estructura especifica información sobre un tipo de campo tomado de un símbolo PDB.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Miembros

`ulAppDomainID`\
ID de la aplicación de la que procede el símbolo. Esto se utiliza para identificar de forma única una instancia de la aplicación.

`guidModule`\
Guid del módulo que contiene este campo.

`symid`\
El identificador del símbolo que corresponde a este campo.

## <a name="remarks"></a>Observaciones

Esta estructura aparece como parte de la `dwKind` unión `TYPE_INFO` en la `TYPE_KIND_PDB` [estructura TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) cuando se establece el campo de la estructura en (un valor de la [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeración).

## <a name="requirements"></a>Requisitos

Encabezado: sh.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también

- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
