---
description: Establece la configuración regional del motor de depuración (DE).
title: 'IDebugEngine2:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8f06ffce2d4fdda772cc29d09057499c32dd6f77
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087930"
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

## <a name="remarks"></a>Observaciones
 El administrador de depuración de la sesión (SDM) llama a este método para propagar la configuración regional del IDE de modo que las cadenas devueltas por el DE estén adaptadas correctamente.

## <a name="see-also"></a>Consulte también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
