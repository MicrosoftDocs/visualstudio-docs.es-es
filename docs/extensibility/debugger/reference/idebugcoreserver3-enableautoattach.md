---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c1bf5f210d9b37b35d43a393a25b1c9df44a7e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691272"
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

#### <a name="parameters"></a>Parámetros
 `rgguidSpecificEngines`

 [in] Matriz de GUID para cada motor de depuración que se va a marcar como asociar en automático.

 `celtSpecificEngines`

 [in] El número de motores especificado en `rgguidSpecificEngines`.

 `pszStartPageUrl`

 [in] La dirección URL de inicio a usar al adjuntar en automático.

 `pbstrSessionID`

 [out] Identificador de la sesión que estaba conectado a la automática.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error. Un código de error es `E_AUTO_ATTACH_NOT_REGISTERED`, lo que indica que el generador de clases auto-attach no se ha registrado.

## <a name="remarks"></a>Comentarios
 Cuando se inicia un programa asociado con la dirección URL especificada, los motores de depuración especificado se inicia automáticamente y se adjuntan.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)