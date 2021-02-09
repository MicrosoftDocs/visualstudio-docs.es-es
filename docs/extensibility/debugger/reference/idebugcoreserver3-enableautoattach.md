---
title: 'IDebugCoreServer3:: EnableAutoAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7873480c979bba4f52203c02864d24aa88cf06cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907995"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Habilita la Asociación automática para los motores de depuración especificados.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parámetros
`rgguidSpecificEngines`\
de Matriz de GUID de cada motor de depuración que se va a marcar como asociación automática.

`celtSpecificEngines`\
de El número de motores especificado en `rgguidSpecificEngines` .

`pszStartPageUrl`\
de Dirección URL de inicio que se va a usar al adjuntar automáticamente.

`pbstrSessionID`\
enuncia IDENTIFICADOR de la sesión que se adjuntó automáticamente.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error. Un código de error es `E_AUTO_ATTACH_NOT_REGISTERED` , que indica que el generador de clases de asociación automática no se ha registrado.

## <a name="remarks"></a>Notas
 Cuando se inicia un programa asociado a la dirección URL especificada, los motores de depuración especificados se inician y adjuntan automáticamente.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
