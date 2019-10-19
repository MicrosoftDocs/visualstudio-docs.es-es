---
title: 'IActiveScriptSite:: OnEnterScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570365"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informa al host de que el motor de scripting ha empezado a ejecutar el código de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting debe llamar a este método en cada entrada o reentrada en el motor de scripting. Por ejemplo, si el script llama a un objeto que, a continuación, activa un evento controlado por el motor de scripting, el motor de scripting debe llamar a `IActiveScriptSite::OnEnterScript` antes de ejecutar el evento y debe llamar al método [IActiveScriptSite:: OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) después de ejecutar el evento. pero antes de volver al objeto que desencadenó el evento. Las llamadas a este método se pueden anidar. Cada llamada a este método requiere una llamada correspondiente a `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)