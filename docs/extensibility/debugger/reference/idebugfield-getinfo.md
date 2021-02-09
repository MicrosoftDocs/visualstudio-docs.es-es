---
title: 'IDebugField:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21d80f222bdea8a8e17a9b74eefb7885cab0c289
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869913"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Este método obtiene información que se pueda mostrar sobre el campo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Parámetros
`dwFields`\
de Combinación de constantes de [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) que selecciona la información que se va a mostrar. Si el campo representa un símbolo, suele ser el nombre y el tipo de símbolo.

`pFieldInfo`\
enuncia Devuelve la información de la estructura de [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) proporcionada.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
