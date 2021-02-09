---
title: 'IDebugPrimitiveTypeField:: GetPrimitiveType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 099456e16ad2bb01329ebff49b13066f1e357ed0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874209"
---
# <a name="idebugprimitivetypefieldgetprimitivetype"></a>IDebugPrimitiveTypeField::GetPrimitiveType
Recupera el tipo primitivo que está asociado a este campo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPrimitiveType (
   DWORD* pdwType
);
```

```csharp
int GetPrimitiveType (
   out uint pdwType
);
```

## <a name="parameters"></a>Parámetros
`pdwType`\
enuncia Valor de la [enumeración CorElementType](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) que representa el tipo primitivo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` .

## <a name="see-also"></a>Vea también
- [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)
