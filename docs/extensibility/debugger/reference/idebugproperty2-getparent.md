---
title: 'IDebugProperty2:: GetParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9855ff168152ed68117569aab939e62da990f81b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850976"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
Obtiene la propiedad primaria de una propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetParent ( 
   IDebugProperty2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugProperty2 ppParent
);
```

## <a name="parameters"></a>Parámetros
`ppParent`\
enuncia Devuelve un objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa el elemento primario de la propiedad.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error. Devuelve `S_GETPARENT_NO_PARENT` si no hay ningún primario.

## <a name="see-also"></a>Vea también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
