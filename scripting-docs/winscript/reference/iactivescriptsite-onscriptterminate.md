---
title: IActiveScriptSite::OnScriptTerminate | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informa al host que la secuencia de comandos ha completado su ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvarResult`  
 [in] Dirección de una variable que contiene el resultado de la secuencia de comandos, o `NULL` si la secuencia de comandos no genera ningún resultado.  
  
 `pexcepinfo`  
 [in] Dirección de un `EXCEPINFO` estructura que contiene información de excepción generada cuando finaliza la secuencia de comandos, o `NULL` si se ha generado ninguna excepción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting llama a este método antes de llamar a la [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) método con la marca SCRIPTSTATE_INITIALIZED establecida, se completa. Este método puede utilizarse para devolver el estado de finalización y los resultados al host. Tenga en cuenta que muchos lenguajes de secuencias de comandos, que se basan en recibir eventos desde el host, tienen intervalos de vida definidos por el host. En este caso, nunca se puede llamar a este método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)