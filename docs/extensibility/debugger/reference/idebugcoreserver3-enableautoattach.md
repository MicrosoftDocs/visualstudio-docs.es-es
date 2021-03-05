---
description: Habilita la Asociación automática para los motores de depuración especificados.
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
ms.openlocfilehash: 644d238db11c117b9068de8f7903361b9712f3aa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163153"
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

## <a name="remarks"></a>Observaciones
 Cuando se inicia un programa asociado a la dirección URL especificada, los motores de depuración especificados se inician y adjuntan automáticamente.

## <a name="see-also"></a>Consulte también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
