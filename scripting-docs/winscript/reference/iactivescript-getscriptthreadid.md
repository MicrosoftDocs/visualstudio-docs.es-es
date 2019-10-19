---
title: 'IActiveScript:: GetScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575704"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Recupera un identificador definido por el motor de scripting para el subproceso asociado al subproceso de Win32 dado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwWin32ThreadID` ,  
 de Identificador de subproceso de un subproceso de Win32 en ejecución en el proceso actual. Use la función [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) para recuperar el identificador del subproceso del subproceso que se está ejecutando actualmente.  
  
 `pstidThread` ,  
 enuncia Dirección de una variable que recibe el identificador del subproceso de script asociado al subproceso de Win32 dado. La interpretación de este identificador se deja en el motor de scripting, pero puede ser simplemente una copia del identificador de subproceso de Windows. Tenga en cuenta que si el subproceso de Win32 finaliza, este identificador se vuelve sin asignar y puede asignarse posteriormente a otro subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado) y, por tanto, se ha producido un error.|  
  
## <a name="remarks"></a>Comentarios  
 El identificador recuperado se puede usar en llamadas posteriores a métodos de control de ejecución de subprocesos de script, como el método [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
 Se puede llamar a este método desde subprocesos no base sin tener como resultado una llamada no base a objetos host o a la interfaz [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)