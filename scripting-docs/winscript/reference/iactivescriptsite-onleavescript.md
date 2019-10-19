---
title: 'IActiveScriptSite:: OnLeaveScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570321"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informa al host de que el motor de scripting ha devuelto la ejecución de código de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting debe llamar a este método antes de devolver el control a una aplicación que realiza la llamada que entró en el motor de scripting. Por ejemplo, si el script llama a un objeto que, a continuación, activa un evento controlado por el motor de scripting, el motor de scripting debe llamar al método [IActiveScriptSite:: OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) antes de ejecutar el evento y debe llamar a `IActiveScriptSite::OnLeaveScript` después de ejecutar el evento. antes de volver al objeto que desencadenó el evento. Las llamadas a este método se pueden anidar. Cada llamada a `IActiveScriptSite::OnEnterScript` requiere una llamada correspondiente a este método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)