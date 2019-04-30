---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9dc3185b644a1045428ead9f2c9851916df3249c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917037"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Devuelve el GUID para todos los posibles motores de depuración (DE) que pueden depurar este programa.

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

#### <a name="parameters"></a>Parámetros
 `celtBuffer`

 [in] El número de GUID de que se va a devolver. Esto también especifica el tamaño máximo de la `rgguidEngines` matriz.

 `rgguidEngines`

 [in, out] Una matriz de GUID DE rellenarse.

 `pceltEngines`

 [out] Devuelve el número real de GUID DE que se devuelven.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o [C#] 0x8007007A si el búfer no es suficientemente grande.

## <a name="remarks"></a>Comentarios
 Con el fin de determinar el número de motores no existe, llame a este método una vez con el `celtBuffer` parámetro establecido en 0 y el `rgguidEngines` parámetro establecido en un valor null. Esto devuelve `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A para C#) y el `pceltEngines` parámetro devuelve el tamaño del búfer necesario.

## <a name="see-also"></a>Vea también
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)