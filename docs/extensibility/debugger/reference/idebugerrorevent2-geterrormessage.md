---
description: Devuelve información que permite la creación de un mensaje de error legible.
title: 'IDebugErrorEvent2:: GetErrorMessage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6f7933441eff3754b90385cfe62dc1314c2d1cb4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153019"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Devuelve información que permite la creación de un mensaje de error legible.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Parámetros
`pMessageType`\
enuncia Devuelve un valor de la enumeración [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) , que describe el tipo de mensaje.

`pbstrErrorFormat`\
enuncia El formato del mensaje final al usuario (vea "Comentarios" para obtener más detalles).

`hrErrorReason`\
enuncia Código de error que trata el mensaje.

`pdwType`\
enuncia Gravedad del error (use las constantes de MB_XXX para `MessageBox` ; por ejemplo, `MB_EXCLAMATION` o `MB_WARNING` ).

`pbstrHelpFileName`\
enuncia Ruta de acceso a un archivo de ayuda (se establece en un valor NULL si no hay ningún archivo de ayuda).

`pdwHelpId`\
enuncia IDENTIFICADOR del tema de ayuda que se va a mostrar (establézcalo en 0 si no hay ningún tema de ayuda).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Se debe dar formato al mensaje de error a lo largo de las líneas de `"What I was doing.  %1"` . `"%1"`Entonces, el llamador reemplazaría por el mensaje de error derivado del código de error (que se devuelve en `hrErrorReason` ). El `pMessageType` parámetro indica al llamador cómo debe mostrarse el mensaje de error final.

## <a name="see-also"></a>Consulte también
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
