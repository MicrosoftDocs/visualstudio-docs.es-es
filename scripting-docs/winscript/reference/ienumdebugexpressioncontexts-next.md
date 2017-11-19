---
title: IEnumDebugExpressionContexts::Next | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugExpressionContexts.Next
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugExpressionContexts::Next
ms.assetid: aa223b0b-f7c1-4368-a59e-677e60133baf
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56b27d74d5677d41535b0f2dfbc2adcb898af789
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugexpressioncontextsnext"></a>IEnumDebugExpressionContexts::Next
Recupera un número especificado de segmentos de la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IDebugExpressionContext**  ppdec,  
   ULONG*                     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de segmentos para recuperar.  
  
 `ppdec`  
 [out] Devuelve una matriz de `IDebugExpressionContext` interfaces que representa los segmentos que se va a recuperar.  
  
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
 [IEnumDebugExpressionContexts (Interfaz)](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)