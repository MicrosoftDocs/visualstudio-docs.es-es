---
title: 'Iactivescriptstats (:: GetStat | Microsoft Docs'
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
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574336"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Devuelve una de las estadísticas del script estándar.  
  
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
 de Especifica la estadística que se va a devolver. Debe ser el valor:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Devuelve el número de instrucciones ejecutadas desde que se inició el script o se restablecieron las estadísticas.|  
  
 `pluHi`  
 enuncia Los bits 32 altos de un entero de 64 bits sin signo que representa la estadística.  
  
 `pluLo`  
 enuncia Los bits 32 bajos de un entero de 64 bits sin signo que representa la estadística.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen, pero no se limitan a los valores de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve una de las estadísticas de script estándar.  
  
## <a name="see-also"></a>Vea también  
 [Iactivescriptstats (:: GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)    
 [IActiveScriptStats (Interfaz)](../../winscript/reference/iactivescriptstats-interface.md)