---
title: IActiveScriptStats::GetStat | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e791661de6d360f747f8d823ad073c2eb81115
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Devuelve una de las estadísticas de la secuencia de comandos estándar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [out] Los 32 bits superiores de un entero de 64 bits sin signo que representa la estadística.  
  
 `pluLo`  
 [out] Los 32 bits inferiores de un entero de 64 bits sin signo que representa la estadística.  
  
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