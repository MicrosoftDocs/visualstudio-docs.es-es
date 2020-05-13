---
title: IDebugErrorEvent2::GetErrorMessage ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730044"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Devuelve información que permite la construcción de un mensaje de error legible por el usuario.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Parámetros
`pMessageType`\
[fuera] Devuelve un valor de la enumeración [MESSAGETYPE,](../../../extensibility/debugger/reference/messagetype.md) que describe el tipo de mensaje.

`pbstrErrorFormat`\
[fuera] El formato del mensaje final para el usuario (consulte "Comentarios" para obtener más información).

`hrErrorReason`\
[fuera] El código de error del que se trata el mensaje.

`pdwType`\
[fuera] Gravedad del error (utilice las constantes MB_XXX para `MessageBox`; por ejemplo, `MB_EXCLAMATION` o `MB_WARNING`).

`pbstrHelpFileName`\
[fuera] Ruta de acceso a un archivo de ayuda (establecido en un valor nulo si no hay ningún archivo de ayuda).

`pdwHelpId`\
[fuera] ID del tema de ayuda que se va a mostrar (establecido en 0 si no hay ningún tema de ayuda).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El mensaje de error debe formatearse a lo largo de las líneas de `"What I was doing.  %1"`. A `"%1"` continuación, el autor de la llamada reemplazará con el mensaje `hrErrorReason`de error derivado del código de error (que se devuelve en ). El `pMessageType` parámetro indica al autor de la llamada cómo se debe mostrar el mensaje de error final.

## <a name="see-also"></a>Vea también
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
