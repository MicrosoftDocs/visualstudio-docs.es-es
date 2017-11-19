---
title: IActiveScriptStats::GetStatEx | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb8adf27811f3046de7b447e537443ef129a8c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Devuelve una estadística de la secuencia de comandos personalizada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guid`  
 [in] Especifica qué estadística para devolver. La semántica de cuál corresponde a un determinado GUID es completamente definido por el motor.  
  
 `pluHi`  
 [out] Los 32 bits superiores de un entero de 64 bits sin signo que representa la estadística.  
  
 `pluLo`  
 [out] Los 32 bits inferiores de un entero de 64 bits sin signo que representa la estadística.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|No se implementa el método.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite usar un motor de secuencia de comandos personalizada devolver estadísticas significativas para un host personalizado.  
  
> [!NOTE]
>  Este método no está implementado actualmente.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats (Interfaz)](../../winscript/reference/iactivescriptstats-interface.md)