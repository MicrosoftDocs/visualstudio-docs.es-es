---
title: IDebugCoreServer3::EnableAutoAttach ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732917"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Habilita la conexión automática para los motores de depuración especificados.

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
[en] Matriz de GUID para cada motor de depuración para marcarcomo auto-adjuntación.

`celtSpecificEngines`\
[en] El número de motores `rgguidSpecificEngines`especificados en .

`pszStartPageUrl`\
[en] La dirección URL de inicio que se va a utilizar al adjuntar automáticamente.

`pbstrSessionID`\
[fuera] ID de la sesión que se adjuntó automáticamente.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve código de error. Un código `E_AUTO_ATTACH_NOT_REGISTERED`de error es , que indica que no se ha registrado el generador de clases de conexión automática.

## <a name="remarks"></a>Observaciones
 Cuando se inicia un programa asociado con la dirección URL especificada, los motores de depuración especificados se inician y adjuntan automáticamente.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
