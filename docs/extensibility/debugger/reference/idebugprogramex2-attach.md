---
title: IDebugProgramEx2::Adjuntar ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722378"
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
[en] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que representa la función de devolución de llamada que el motor de depuración asociado envía eventos a.

`dwReason`\
[en] Valor de la [enumeración ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeración que describe el motivo de la operación de asociación.

`pSession`\
[en] Valor que identifica de forma única la sesión que se asocia al programa.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve un código de error. Este método `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` debe devolver si el programa ya está asociado.

## <a name="remarks"></a>Observaciones
 El puerto que contiene el programa `pSession` puede utilizar el valor para determinar qué sesión está intentando adjuntar al programa. Por ejemplo, si un puerto permite que solo una sesión de depuración se asocie a un proceso a la vez, el puerto puede determinar si la misma sesión ya está asociada a otros programas en el proceso.

> [!NOTE]
> La interfaz `pSession` que se pasa debe tratarse solo como una cookie, un valor que identifica de forma única el administrador de depuración de sesión que se adjunta a este programa; ninguno de los métodos de la interfaz suministrada son funcionales.

## <a name="see-also"></a>Vea también
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
