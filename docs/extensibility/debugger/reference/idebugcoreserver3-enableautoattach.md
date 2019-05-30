---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9eb8beed7f32e9c6fb64212f73a41a35544259bb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326972"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Habilita la asociación automática para los motores de depuración especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parámetros
`rgguidSpecificEngines`\
[in] Matriz de GUID para cada motor de depuración que se va a marcar como asociar en automático.

`celtSpecificEngines`\
[in] El número de motores especificado en `rgguidSpecificEngines`.

`pszStartPageUrl`\
[in] La dirección URL de inicio a usar al adjuntar en automático.

`pbstrSessionID`\
[out] Identificador de la sesión que estaba conectado a la automática.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error. Un código de error es `E_AUTO_ATTACH_NOT_REGISTERED`, lo que indica que el generador de clases auto-attach no se ha registrado.

## <a name="remarks"></a>Comentarios
 Cuando se inicia un programa asociado con la dirección URL especificada, los motores de depuración especificado se inicia automáticamente y se adjuntan.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)