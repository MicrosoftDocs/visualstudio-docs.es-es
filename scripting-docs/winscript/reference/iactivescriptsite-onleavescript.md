---
title: IActiveScriptSite::OnLeaveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 7d08d58fc788d2d10ed044808ca40a5f4ea929c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093163"
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