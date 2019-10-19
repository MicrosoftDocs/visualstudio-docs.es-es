---
title: 'Iactivescriptstats (:: ResetStats | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.ResetStats
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::ResetStats
ms.assetid: d98276fc-ad47-4e7b-aae4-254d63aece77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2767bb1e2cce3a11661ebaca37e66d33f95beb2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577966"
---
# <a name="iactivescriptstatsresetstats"></a>IActiveScriptStats::ResetStats
Restablece las estadísticas para este script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ResetStats();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método restablece las estadísticas para este script.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptStats (Interfaz)](../../winscript/reference/iactivescriptstats-interface.md)