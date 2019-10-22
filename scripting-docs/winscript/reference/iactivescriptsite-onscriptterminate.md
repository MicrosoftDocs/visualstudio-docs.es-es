---
title: 'IActiveScriptSite:: OnScriptTerminate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570206"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informa al host de que se ha completado la ejecución del script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvarResult`  
 de Dirección de una variable que contiene el resultado del script o `NULL` si el script no generó ningún resultado.  
  
 `pexcepinfo`  
 de Dirección de una estructura de `EXCEPINFO` que contiene la información de excepción generada cuando terminó el script o `NULL` si no se generó ninguna excepción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting llama a este método antes de que se complete la llamada al método [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) , con la marca SCRIPTSTATE_INITIALIZED establecida. Este método se puede utilizar para devolver el estado de finalización y los resultados al host. Tenga en cuenta que muchos lenguajes de scripts, que se basan en el receptor de eventos del host, tienen intervalos de vida definidos por el host. En este caso, nunca se puede llamar a este método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)