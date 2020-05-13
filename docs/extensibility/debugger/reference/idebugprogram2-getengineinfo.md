---
title: IDebugProgram2::GetEngineInfo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53f16a3ef6bd1328d73c8a6c71c666968d5564d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722831"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
Obtiene el nombre y el GUID del motor de depuración (DE) que ejecuta este programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEngineInfo( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo( 
   out string pbstrEngine,
   out GUID   pguidEngine
);
```

## <a name="parameters"></a>Parámetros
`pbstrEngine`\
[fuera] Devuelve el nombre de la DE que ejecuta este programa.

`pguidEngine`\
[fuera] Devuelve el GUID de la DE que ejecuta este programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cada DE define su propio GUID para la identificación.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
