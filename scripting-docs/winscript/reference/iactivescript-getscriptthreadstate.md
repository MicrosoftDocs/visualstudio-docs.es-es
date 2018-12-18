---
title: IActiveScript::GetScriptThreadState | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641265"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Recupera el estado actual de un subproceso de la secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stidThread`  
 [in] Identificador del subproceso para el que se desea el estado, o uno de los identificadores de subproceso especiales siguientes:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|El subproceso base; es decir, se crea una instancia en el subproceso en el que el scripting del motor.|  
|SCRIPTTHREADID_CURRENT|El subproceso actualmente en ejecución.|  
  
 `pstsState`  
 [out] Dirección de una variable que recibe el estado del subproceso indicado. El estado se indica mediante uno de los valores de constantes con nombre definidos por el [SCRIPTTHREADSTATE (enumeración)](../../winscript/reference/scriptthreadstate-enumeration.md) enumeración. Si este parámetro no identifica el subproceso actual, el estado puede cambiar en cualquier momento.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting se aún no ha cargado o inicializar).|  
  
## <a name="remarks"></a>Comentarios  
 Este método se pueda llamar desde subprocesos no sea de base sin resultante en una llamada no sea de base a los objetos de host o a la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)