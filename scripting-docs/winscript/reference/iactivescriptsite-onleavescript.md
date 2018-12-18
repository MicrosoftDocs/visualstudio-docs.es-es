---
title: IActiveScriptSite::OnLeaveScript | Documentos de Microsoft
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
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725175"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informa al host que ha devuelto el motor de scripting de ejecución de código de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting debe llamar a este método antes de devolver el control a una aplicación que realiza la llamada que especificó el motor de scripting. Por ejemplo, si la secuencia de comandos llama a un objeto que activa un evento como controlado por el motor de scripting, el motor de scripting debe llamar a la [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) método antes de ejecutar el evento y debe llamar a `IActiveScriptSite::OnLeaveScript`después de ejecutar el evento antes de devolver el objeto que desencadenó el evento. Se pueden anidar las llamadas a este método. Todas las llamadas a `IActiveScriptSite::OnEnterScript` requiere una llamada correspondiente a este método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)