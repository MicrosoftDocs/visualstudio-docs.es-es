---
title: 'IDebugEngine3:: SetEngineGuid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae151484a7c2fd5828888a8a551b710c6fda44c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730757"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
Este método establece el del motor de depuración (DE) `GUID` .

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetEngineGuid(
   GUID* guidEngine
);
```

```csharp
int SetEngineGuid(
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Parámetros
`guidEngine`\
[in] `GUID` del motor.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

## <a name="see-also"></a>Vea también
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
