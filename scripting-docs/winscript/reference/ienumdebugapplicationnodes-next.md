---
title: IEnumDebugApplicationNodes::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Next
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f826ce91ba99c5bb697a346b40a6b7f97b6f5914
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951624"
---
# <a name="ienumdebugapplicationnodesnext"></a>IEnumDebugApplicationNodes::Next
Recupera un número especificado de segmentos de la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de segmentos se van a recuperar.  
  
 `pprddp`  
 [out] Devuelve una matriz de `IDebugApplicationNode` interfaces que representa los segmentos que se va a recuperar.  
  
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
 [IEnumDebugApplicationNodes (Interfaz)](../../winscript/reference/ienumdebugapplicationnodes-interface.md)