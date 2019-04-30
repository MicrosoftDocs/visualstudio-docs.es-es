---
title: IActiveScript::GetScriptState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f9f3bedee9af9ae3cb145108d801f252267d5d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935753"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Recupera el estado actual del motor de scripting. Este método se pueda llamar desde subprocesos no son de base sin resultante en una llamada que no sea de base a los objetos de host o a la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pss`  
 [out] Dirección de una variable que recibe un valor definido en el [SCRIPTSTATE (enumeración)](../../winscript/reference/scriptstate-enumeration.md) enumeración. El valor indica el estado actual del motor de scripting asociado al subproceso que realiza la llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_POINTER` si se ha especificado un puntero no válido.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)