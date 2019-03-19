---
title: IActiveScriptStats::GetStatEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f1585e335fac0072eba48494bf8c27736a47f41
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149174"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Devuelve una estadística de script personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guid`  
 [in] Especifica qué estadística para devolver. La semántica de cuál corresponde a un determinado GUID está completamente definido por el motor.  
  
 `pluHi`  
 [out] 32 bits superiores de un entero de 64 bits sin signo que representa la estadística.  
  
 `pluLo`  
 [out] 32 bits inferiores de un entero de 64 bits sin signo que representa la estadística.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|No se implementa el método.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite que un motor de script personalizado devolver estadísticas significativas para un host personalizado.  
  
> [!NOTE]
>  Este método no está implementado actualmente.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats (Interfaz)](../../winscript/reference/iactivescriptstats-interface.md)