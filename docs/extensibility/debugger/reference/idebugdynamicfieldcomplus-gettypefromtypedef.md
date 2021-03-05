---
description: Recupera un tipo a partir de su token.
title: 'IDebugDynamicFieldCOMPlus:: GetTypeFromTypeDef | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypeFromTypeDef
- IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68f0747c61f1e2c19ea1abde309f8fab437ecc84
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154111"
---
# <a name="idebugdynamicfieldcomplusgettypefromtypedef"></a>IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
Recupera un tipo a partir de su token.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetTypeFromTypeDef(
   ULONG32       ulAppDomainID,
   GUID          guidModule,
   _mdToken      tokClass,
   IDebugField** ppType
);
```

```csharp
int GetTypeFromTypeDef(
   uint            ulAppDomainID,
   Guid            guidModule,
   int             tokClass,
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parámetros
`ulAppDomainID`\
de Identificador del dominio de aplicación.

`guidModule`\
de Identificador único del módulo.

`tokClass`\
de Token que representa el tipo.

`ppType`\
enuncia Devuelve un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que contiene el tipo.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
