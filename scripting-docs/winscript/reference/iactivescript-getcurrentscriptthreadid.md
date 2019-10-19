---
title: 'IActiveScript:: GetCurrentScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575772"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Recupera un identificador definido por el motor de scripting para el subproceso que se está ejecutando actualmente. El identificador se puede utilizar en llamadas posteriores a métodos de control de ejecución de subprocesos de script, como el método [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstidThread`  
 enuncia Dirección de una variable que recibe el identificador del subproceso de script asociado al subproceso actual. La interpretación de este identificador se deja en el motor de scripting, pero puede ser simplemente una copia del identificador de subproceso de Windows. Si el subproceso de Win32 finaliza, este identificador se vuelve sin asignar y se puede asignar posteriormente a otro subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_POINTER` si se especificó un puntero no válido.  
  
## <a name="remarks"></a>Comentarios  
 Se puede llamar a este método desde subprocesos no base sin tener como resultado una llamada no base a objetos host o a la interfaz [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)