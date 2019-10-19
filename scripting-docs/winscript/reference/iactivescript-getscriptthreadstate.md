---
title: 'IActiveScript:: GetScriptThreadState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578009"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Recupera el estado actual de un subproceso de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stidThread`  
 de Identificador del subproceso para el que se desea el estado o uno de los siguientes identificadores de subproceso especial:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Subproceso base; es decir, el subproceso en el que se creó la instancia del motor de scripting.|  
|SCRIPTTHREADID_CURRENT|Subproceso que se está ejecutando actualmente.|  
  
 `pstsState`  
 enuncia Dirección de una variable que recibe el estado del subproceso indicado. El estado se indica mediante uno de los valores constantes con nombre definidos por la enumeración de [enumeración scriptthreadstate (](../../winscript/reference/scriptthreadstate-enumeration.md) . Si este parámetro no identifica el subproceso actual, el estado puede cambiar en cualquier momento.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado).|  
  
## <a name="remarks"></a>Comentarios  
 Se puede llamar a este método desde subprocesos no base sin tener como resultado una llamada no base a objetos host o a la interfaz [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)