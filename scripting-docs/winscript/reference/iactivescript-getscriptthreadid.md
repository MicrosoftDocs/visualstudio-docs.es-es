---
title: IActiveScript::GetScriptThreadID | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Recupera un identificador de scripting motor-definido por el subproceso asociado al subproceso de Win32 determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwWin32ThreadID` ,  
 [in] Identificador del subproceso de un subproceso de Win32 en ejecución en el proceso actual. Use la [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) función para recuperar el identificador del subproceso del subproceso actualmente en ejecución.  
  
 `pstidThread` ,  
 [out] Dirección de una variable que recibe el identificador de subproceso de script asociado al subproceso de Win32 determinado. La interpretación de este identificador se deja al motor de scripting, pero puede ser simplemente una copia del identificador de subproceso de Windows. Tenga en cuenta que si finaliza el subproceso de Win32, este identificador se convierte en sin asignar y posteriormente se puede asignar a otro subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting se aún no ha cargado o inicializar) y, por tanto, no se pudo.|  
  
## <a name="remarks"></a>Comentarios  
 El identificador recuperado se puede utilizar en llamadas posteriores a métodos de control de ejecución de subprocesos de script como el [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) método.  
  
 Este método se pueda llamar desde subprocesos no sea de base sin resultante en una llamada no sea de base a los objetos de host o a la [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)