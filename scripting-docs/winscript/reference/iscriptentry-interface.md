---
title: Interfaz Iscriptentry (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575390"
---
# <a name="iscriptentry-interface"></a>IScriptEntry (Interfaz)
Un objeto que implementa la interfaz `IScriptEntry` representa un bloque de script o un objeto de función.  
  
 Además de los métodos heredados de `IScriptNode`, la interfaz de `IScriptEntry` expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Devuelve el texto que corresponde al cuerpo de un `IScriptEntry` bloque de script, función o Scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Devuelve el nombre de elemento que identifica un objeto `IScriptEntry`.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|En el caso de las entradas que representan un único objeto (como una función), devuelve el nombre del objeto.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Devuelve la posición inicial y la longitud de una entrada.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Devuelve información de tipo para un objeto de función de `IScriptEntry`.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Devuelve el texto que corresponde a un bloque de script de `IScriptEntry`, o el código fuente incluido en un controlador de eventos `IScriptScriptlet`.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Establece el texto que se encuentra en el cuerpo de un `IScriptEntry` bloque de script o un Scriptlet de `IScriptScriptlet`.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Establece el nombre de elemento que identifica un objeto `IScriptEntry`.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|En el caso de las entradas que representan un solo objeto (como una función), establece el nombre del objeto.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Establece la información de tipo para un objeto de función de `IScriptEntry`.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Establece el texto que corresponde a un `IScriptEntry` bloque de script o el código fuente incluido en un controlador de eventos `IScriptScriptlet`.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Authoring (Interfaces)](../../winscript/reference/active-script-authoring-interfaces.md)