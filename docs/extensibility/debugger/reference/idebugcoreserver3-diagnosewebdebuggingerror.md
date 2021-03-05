---
description: Intenta determinar por qué se produjo un error en la Asociación automática.
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95e54add3616fa0ec97f4114b4cd628213e752f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154696"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Intenta determinar por qué se produjo un error en la Asociación automática.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parámetros
`pszUrl`\
de No se usa actualmente; siempre se debe establecer en un valor null.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. A continuación se muestran otros códigos de retorno típicos:

|Código|Descripción|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|No se puede determinar por qué el servidor remoto no pudo iniciar la depuración.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|No se puede depurar en el servidor remoto, posiblemente debido a permisos insuficientes o a que el verbo DEBUG no está habilitado.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|El servidor Web se ha bloqueado y está bloqueando el verbo DEBUG, que es necesario para habilitar la depuración.|

## <a name="see-also"></a>Consulte también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
