---
title: IDebugProgramNode2::GetEngineInfo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2e74ba3c0f826314818bc883778a6364ff3fb6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722103"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Obtiene el nombre y el identificador del motor de depuración (DE) que ejecuta un programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>Parámetros
`pbstrEngine`\
[fuera] Devuelve el nombre de la DE que ejecuta el programa (específico de C+): puede ser un puntero nulo que indica que el autor de la llamada no está interesado en el nombre del motor).

`pguidEngine`\
[fuera] Devuelve el identificador único global de la DE que ejecuta el programa (específico de C++: puede ser un puntero nulo que indica que el autor de la llamada no está interesado en el GUID del motor).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
