---
description: Obtiene el nombre de usuario del proveedor del puerto.
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04ad8bf6ba572a1f9e14e26ef2ca37d021f6e3a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166208"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtiene el nombre de usuario del proveedor del puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Parámetros
`pbstrUserName`\
enuncia Cadena que contiene el nombre de usuario.

## <a name="return-value"></a>Valor devuelto
 Si el método se realiza correctamente, devuelve `S_OK`. En caso contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 `GetUserName` Devuelve el nombre de usuario que se muestra en la columna **nombre de usuario** del cuadro de diálogo **asociar al proceso** . Para ver el cuadro de diálogo **asociar al proceso** , haga clic en **asociar al proceso** en el menú **herramientas** del [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE).

## <a name="see-also"></a>Consulte también
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
