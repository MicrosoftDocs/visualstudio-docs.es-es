---
title: IActiveScriptSite::OnEnterScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ccef1b2bf63c4421843d3a33cab2e4f471a48251
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346519"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informa al host que el motor de scripting ha empezado a ejecutar el código de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting debe llamar a este método en cada entrada y la reentrada en el motor de scripting. Por ejemplo, si el script llama a un objeto que activa un evento como controlado por el motor de scripting, el motor de scripting debe llamar a `IActiveScriptSite::OnEnterScript` antes de ejecutar el evento y debe llamar a la [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) método después de ejecutar el evento, pero antes de devolver el objeto que desencadenó el evento. Se pueden anidar las llamadas a este método. Cada llamada a este método requiere una llamada correspondiente a `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)