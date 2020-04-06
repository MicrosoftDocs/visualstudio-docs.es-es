---
title: IDebugProcessSecurity::GetUserName ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723260"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtiene el nombre de usuario del proveedor de puertos.

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
[fuera] Cadena que contiene el nombre de usuario.

## <a name="return-value"></a>Valor devuelto
 Si el método se realiza correctamente, devuelve `S_OK`. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 `GetUserName`devuelve el nombre de usuario que se muestra en la columna Nombre de **usuario** del cuadro de diálogo **Adjuntar al proceso.** Para ver el cuadro de diálogo **Asociar al proceso,** [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] haga clic en Asociar al **proceso** en el menú **Herramientas** del entorno de desarrollo integrado (IDE).

## <a name="see-also"></a>Vea también
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
