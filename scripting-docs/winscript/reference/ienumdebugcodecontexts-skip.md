---
title: IEnumDebugCodeContexts::Skip | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugCodeContexts.Skip
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugCodeContexts::Skip
ms.assetid: ba917f57-f7a9-419f-96d6-8f4378b12c57
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d053fdfe079636755acf125f5a2c02f8690b2a53
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugcodecontextsskip"></a>IEnumDebugCodeContexts::Skip
Omite un número especificado de segmentos en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] Número de segmentos en la secuencia de enumeración que se va a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método omite un número especificado de segmentos en una secuencia de enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugCodeContexts (Interfaz)](../../winscript/reference/ienumdebugcodecontexts-interface.md)