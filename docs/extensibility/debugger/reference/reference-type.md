---
description: Especifica el tipo de referencia.
title: REFERENCE_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e38d23c855af098f2c32e60c1e3fa7d8fece5502
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079454"
---
# <a name="reference_type"></a>REFERENCE_TYPE
Especifica el tipo de referencia.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
typedef DWORD REFERENCE_TYPE;
```

```csharp
public enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
```

## <a name="fields"></a>Campos
 `REF_TYPE_WEAK`\
 Especifica una referencia débil. No se puede combinar con `REF_TYPE_STRONG` .

 `REF_TYPE_STRONG`\
 Especifica una referencia segura. No se puede combinar con `REF_TYPE_WEAK` .

## <a name="remarks"></a>Observaciones
 Se usa como `dwRefType` miembro de la estructura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .

 Se pasa como un parámetro al método [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)
