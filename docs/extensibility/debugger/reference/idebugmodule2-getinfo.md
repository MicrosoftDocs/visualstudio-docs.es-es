---
title: 'IDebugModule2:: GetInfo | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 205a32c0c7c6bb10b8b0a58e62f5d6ba5cdca91f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941705"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Obtiene información acerca de este módulo.

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
de Combinación de marcas de la enumeración [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) que especifican los campos de que `pInfo` se van a rellenar.

`pInfo`\
[in, out] [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estructura que se rellena con una descripción del módulo.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 La estructura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) contiene el nombre del módulo que se muestra en la ventana **módulos** .

## <a name="see-also"></a>Vea también
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
