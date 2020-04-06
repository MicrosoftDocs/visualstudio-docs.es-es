---
title: IDebugEngine3::SetJustMyCodeState ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9930f8ecf0c2f9b6fff4ce1c9e3edb935c5a7912
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730673"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Este método indica al motor de depuración acerca de la información de estado JustMyCode.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parámetros
`fUpdate`\
[en] Distinto de`TRUE`cero ( ) para`FALSE`actualizar la información actual, cero ( ) para restablecer toda la información (ignorando cualquier cosa previamente establecida).

`dwModules`\
[en] Número de estructuras de información en`rgJMCSpec.`

`rgJMCSpec`\
[en] Matriz de [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) estructuras que se va a utilizar.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario, devuelve el código de error.

## <a name="remarks"></a>Observaciones
 JustMyCode es el concepto de depurar solo el código que pertenece a un usuario e ignorar todo el código intermedio, como el código del sistema, incluso si el código fuente está disponible para ese código del sistema.

## <a name="see-also"></a>Vea también
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
