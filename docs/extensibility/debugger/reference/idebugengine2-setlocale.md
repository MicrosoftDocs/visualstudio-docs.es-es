---
title: 'IDebugEngine2:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e43d8d13f34b8477ab870c80842ff33eef72a7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878921"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Establece la configuración regional del motor de depuración (DE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>Parámetros
`wLangID`\
de Especifica la configuración regional del idioma. Por ejemplo, 1033 para inglés.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 El administrador de depuración de la sesión (SDM) llama a este método para propagar la configuración regional del IDE de modo que las cadenas devueltas por el DE estén adaptadas correctamente.

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
