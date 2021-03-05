---
description: Adjunte una sesión a un programa.
title: 'IDebugProgramEx2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa9a66bdec3da9b6d18772b4ff2c85a7874bde6c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150151"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Adjunte una sesión a un programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Parámetros
`pCallback`\
de Un objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que representa la función de devolución de llamada a la que el motor de depuración asociado envía eventos.

`dwReason`\
de Un valor de la enumeración [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) que describe la razón de la operación de adjuntar.

`pSession`\
de Valor que identifica de forma única la sesión que se está asociando al programa.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error. Este método debe devolver `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` si el programa ya está asociado.

## <a name="remarks"></a>Observaciones
 El puerto que contiene el programa puede utilizar el valor de `pSession` para determinar qué sesión está intentando adjuntar al programa. Por ejemplo, si un puerto solo permite una sesión de depuración para asociar a un proceso a la vez, el puerto puede determinar si la misma sesión ya está adjunta a otros programas del proceso.

> [!NOTE]
> La interfaz que se pasa `pSession` se trata únicamente como una cookie, un valor que identifica de forma única el administrador de depuración de la sesión que se adjunta a este programa; ninguno de los métodos de la interfaz proporcionada es funcional.

## <a name="see-also"></a>Consulte también
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
