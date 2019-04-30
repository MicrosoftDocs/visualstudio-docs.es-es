---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8340e9fd9e5f38963a9de78e2974404f600deef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917459"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtiene el nombre de usuario desde el proveedor del puerto.

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

#### <a name="parameters"></a>Parámetros
 `pbstrUserName`

 [out] Una cadena que contiene el nombre de usuario.

## <a name="return-value"></a>Valor devuelto
 Si el método se realiza correctamente, devuelve `S_OK`. En caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 `GetUserName` Devuelve el nombre de usuario que se muestra en el **nombre de usuario** columna de la **asociar al proceso** cuadro de diálogo. Para ver el **asociar al proceso** cuadro de diálogo, haga clic en **asociar al proceso** en el **herramientas** menú en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE).

## <a name="see-also"></a>Vea también
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)