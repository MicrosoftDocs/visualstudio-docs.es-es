---
description: Obtiene el nombre y el identificador del motor de depuración (DE) que ejecuta un programa.
title: 'IDebugProgramNode2:: GetEngineInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a902db31cb4d48810e673e7807bd3944c2a875
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053534"
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
enuncia Devuelve el nombre de la ejecución del programa (específico de C++: puede ser un puntero nulo que indica que el llamador no está interesado en el nombre del motor).

`pguidEngine`\
enuncia Devuelve el identificador único global de de la ejecución del programa (específico de C++: puede ser un puntero nulo que indica que el llamador no está interesado en el GUID del motor).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
