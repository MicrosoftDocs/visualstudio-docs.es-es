---
title: IEnumRemoteDebugApplications::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Next
ms.assetid: 33f6c620-6dd3-4057-b982-b88a7a1f02b4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b14874891e739fc95b877e41e76559a1ab0060a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963242"
---
# <a name="ienumremotedebugapplicationsnext"></a>IEnumRemoteDebugApplications::Next
El `Next` método recupera un número especificado de segmentos de la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Next(  
   ULONG                      celt,  
   IRemoteDebugApplication**  ppda,  
   ULONG*                     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de segmentos se van a recuperar.  
  
 `ppda`  
 [out] Devuelve una matriz de `IRemoteDebugApplication` interfaces que representa los segmentos que se va a recuperar.  
  
 `pceltFetched`  
 [out] El número real de capturado por el enumerador de segmentos.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera un número especificado de segmentos de la secuencia de enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IEnumRemoteDebugApplications (Interfaz)](../../winscript/reference/ienumremotedebugapplications-interface.md)