---
title: IDebugModule2::GetInfo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c68c583702d7def5a7bff3ee40a9b8b2c537bb31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726964"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Obtiene información sobre este módulo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

## <a name="parameters"></a>Parámetros
`dwFields`\
[en] Una combinación de [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) indicadores de la `pInfo` MODULE_INFO_FIELDS enumeración que especifican qué campos de se van a rellenar.

`pInfo`\
[adentro, fuera] Una [estructura MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) que se rellena con una descripción del módulo.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La estructura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) contiene el nombre del módulo que se muestra en la ventana **Módulos.**

## <a name="see-also"></a>Vea también
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
