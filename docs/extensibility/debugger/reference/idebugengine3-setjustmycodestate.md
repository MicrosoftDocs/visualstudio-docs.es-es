---
description: Este método indica al motor de depuración sobre la información de estado JustMyCode.
title: 'IDebugEngine3:: SetJustMyCodeState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a81fa4bda506cf1be27f658b071910e7c8ccd8a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153708"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Este método indica al motor de depuración sobre la información de estado JustMyCode.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
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
de Distinto de cero ( `TRUE` ) para actualizar la información actual, cero ( `FALSE` ) para restablecer toda la información (omitiendo todo lo establecido anteriormente).

`dwModules`\
de Número de estructuras de información en `rgJMCSpec.`

`rgJMCSpec`\
de Matriz de estructuras [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) que se va a usar.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

## <a name="remarks"></a>Observaciones
 JustMyCode es el concepto de depurar solo el código que pertenece a un usuario y omitir todo el código intermedio, como el código del sistema, incluso si el código fuente está disponible para ese código del sistema.

## <a name="see-also"></a>Consulte también
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
