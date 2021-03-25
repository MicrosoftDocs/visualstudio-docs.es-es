---
description: Obtiene el nombre de usuario del proveedor del puerto.
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42a13075b233d5b0fe70b314a4b2d025a2a4c7d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076308"
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
