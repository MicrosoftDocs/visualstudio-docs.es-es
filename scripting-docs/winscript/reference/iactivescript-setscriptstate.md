---
title: 'IActiveScript:: SetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577989"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Coloca el motor de scripting en el estado especificado. Se puede llamar a este método desde subprocesos no base sin tener como resultado una llamada no base a objetos host o a la interfaz [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ss`  
 de Establece el motor de scripting en el estado especificado. Puede ser uno de los valores definidos en la enumeración de [enumeración scriptstate (](../../winscript/reference/scriptstate-enumeration.md) .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_FAIL`|El motor de scripting no admite la transición de vuelta al estado inicializado. El host debe descartar este motor de scripting y crear, inicializar y cargar un nuevo motor de scripting para lograr el mismo efecto.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado) y, por tanto, se ha producido un error.|  
|`OLESCRIPT_S_PENDING`|El método se puso en cola correctamente, pero el estado todavía no ha cambiado. Cuando el estado cambia, se volverá a llamar al sitio a través del método [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|El método se realizó correctamente, pero el script ya estaba en el estado especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de los Estados del motor de scripting, consulte la sección Estados del motor de scripts de [Windows Script](../../winscript/windows-script-engines.md) engines.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript:: Clone](../../winscript/reference/iactivescript-clone.md)    
 [IActiveScript:: GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)    
 [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)    
 [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)    
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)