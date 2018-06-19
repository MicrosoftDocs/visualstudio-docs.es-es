---
title: IDebugProgramEngines2::EnumPossibleEngines | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d30eb28398569aa3d14b4a7dd363abac785f352c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116079"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Devuelve el GUID de todos los posibles motores de depuración (Alemania) que pueden depurar este programa.  
  
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
 [in] El número de GUID de Alemania que se va a devolver. También especifica el tamaño máximo de la `rgguidEngines` matriz.  
  
 `rgguidEngines`  
 [entrada, salida] Una matriz de GUID de Alemania que deben rellenarse.  
  
 `pceltEngines`  
 [out] Devuelve el número real de GUID DE que se devuelven.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o [C#] 0x8007007A si el búfer no es suficientemente grande.  
  
## <a name="remarks"></a>Comentarios  
 Con el fin de determinar el número de motores no existe, llame a este método una vez con la `celtBuffer` parámetro establecido en 0 y el `rgguidEngines` parámetro establecido en un valor null. Esto devuelve `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A para C#) y el `pceltEngines` parámetro devuelve el tamaño necesario del búfer.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)