---
title: IDebugProgramEngines2::EnumPossibleEngines ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722430"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Devuelve los GUID para todos los posibles motores de depuración (DE) que pueden depurar este programa.

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
[en] El número de GUID DE que se van a devolver. Esto también especifica el tamaño `rgguidEngines` máximo de la matriz.

`rgguidEngines`\
[adentro, fuera] Matriz de GUID DE que se van a rellenar.

`pceltEngines`\
[fuera] Devuelve el número real de GUID DE que se devuelven.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o [C-] 0x8007007A si el búfer no es lo suficientemente grande.

## <a name="remarks"></a>Observaciones
 Para determinar cuántos motores hay, llame a este `celtBuffer` método una vez `rgguidEngines` con el parámetro establecido en 0 y el parámetro establecido en un valor nulo. Esto `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` devuelve (0x8007007A para C-), y el `pceltEngines` parámetro devuelve el tamaño necesario del búfer.

## <a name="see-also"></a>Vea también
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
