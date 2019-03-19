---
title: IActiveScriptSite::OnLeaveScript | Microsoft Docs
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
ms.openlocfilehash: da39058a8f069c4799835108372d11849d86444e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160750"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informa al host que ha devuelto el motor de scripting de ejecutar código de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting debe llamar a este método antes de devolver el control a una aplicación que realiza la llamada que especificó el motor de scripting. Por ejemplo, si el script llama a un objeto que activa un evento como controlado por el motor de scripting, el motor de scripting debe llamar a la [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) método antes de ejecutar el evento y debe llamar a `IActiveScriptSite::OnLeaveScript`después de ejecutar el evento antes de devolver el objeto que desencadenó el evento. Se pueden anidar las llamadas a este método. Cada llamada a `IActiveScriptSite::OnEnterScript` requiere una llamada correspondiente a este método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)