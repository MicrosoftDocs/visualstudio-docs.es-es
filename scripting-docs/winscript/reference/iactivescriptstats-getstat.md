---
title: IActiveScriptStats::GetStat | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8befb3da4e4b6f060a5f58aedec3604afe70aefb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159054"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Devuelve una de las estadísticas de la secuencia de comandos estándar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stid`  
 [in] Especifica qué estadística para devolver. Debe ser el valor:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Devuelve el número de instrucciones ejecutadas desde que se inició la secuencia de comandos o se restablecieron las estadísticas.|  
  
 `pluHi`  
 [out] 32 bits superiores de un entero de 64 bits sin signo que representa la estadística.  
  
 `pluLo`  
 [out] 32 bits inferiores de un entero de 64 bits sin signo que representa la estadística.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Los valores posibles incluyen, pero no se limitan a los valores en la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve una de las estadísticas de la secuencia de comandos estándar.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats (Interfaz)](../../winscript/reference/iactivescriptstats-interface.md)