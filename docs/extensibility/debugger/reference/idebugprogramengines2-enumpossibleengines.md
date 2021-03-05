---
description: Devuelve los GUID para todos los motores de depuración posibles (DE) que pueden depurar este programa.
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5719728637f26ed61283578565470b39fc60455
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151589"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Devuelve los GUID para todos los motores de depuración posibles (DE) que pueden depurar este programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Parámetros
`celtBuffer`\
de Número de GUID que se van a devolver. También especifica el tamaño máximo de la `rgguidEngines` matriz.

`rgguidEngines`\
[in, out] Matriz de de GUID que se va a rellenar.

`pceltEngines`\
enuncia Devuelve el número real de GUID que se devuelven.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o [C#] 0x8007007A si el búfer no es suficientemente grande.

## <a name="remarks"></a>Observaciones
 Con el fin de determinar cuántos motores hay, llame una vez a este método con el `celtBuffer` parámetro establecido en 0 y el `rgguidEngines` parámetro establecido en un valor null. Devuelve `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A para C#) y el `pceltEngines` parámetro devuelve el tamaño necesario del búfer.

## <a name="see-also"></a>Consulte también
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
