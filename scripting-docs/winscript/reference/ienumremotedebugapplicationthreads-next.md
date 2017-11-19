---
title: IEnumRemoteDebugApplicationThreads::Next | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumRemoteDebugApplicationThreads.Next
apilocation: pdm.dll
helpviewer_keywords: IEnumRemoteDebugApplicationThreads::Next
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8ce0dc7c77cd3b58f388ab63a9d5a3573c93419
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ienumremotedebugapplicationthreadsnext"></a>IEnumRemoteDebugApplicationThreads::Next
El `Next` método recupera un número especificado de segmentos de la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de segmentos para recuperar.  
  
 `pprdat`  
 [out] Devuelve una matriz de `IRemoteDebugApplicationThread` interfaces que representa los segmentos que se va a recuperar.  
  
 `pceltFetched`  
 [out] El número real de segmentos capturados por el enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera un número especificado de segmentos de la secuencia de enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IEnumRemoteDebugApplicationThreads (Interfaz)](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)