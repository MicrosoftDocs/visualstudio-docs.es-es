---
title: IActiveScript::GetCurrentScriptThreadID | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Recupera un identificador de scripting motor-definido por el subproceso actualmente en ejecución. El identificador se puede utilizar en llamadas posteriores a métodos de control de la ejecución de subprocesos de script como el [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstidThread`  
 [out] Dirección de una variable que recibe el identificador de subproceso de secuencia de comandos asociado al subproceso actual. La interpretación de este identificador se deja al motor de scripting, pero puede ser simplemente una copia del identificador de subproceso de Windows. Si finaliza el subproceso de Win32, este identificador se convierte en sin asignar y posteriormente se puede asignar a otro subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_POINTER` si se especificó un puntero no válido.  
  
## <a name="remarks"></a>Comentarios  
 Este método se pueda llamar desde subprocesos no sea de base sin resultante en una llamada no sea de base a los objetos de host o a la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)