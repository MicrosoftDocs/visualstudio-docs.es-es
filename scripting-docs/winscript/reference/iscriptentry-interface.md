---
title: IScriptEntry (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a785be8777cf3400f7723c24f1022bad6e22e330
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentry-interface"></a>IScriptEntry (Interfaz)
Un objeto que implementa el `IScriptEntry` interfaz representa un bloque de script o un objeto de función.  
  
 Además de los métodos heredados de `IScriptNode`, el `IScriptEntry` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Devuelve el texto que corresponde al cuerpo de un `IScriptEntry` scriptlet, bloque de la función o bloque de script.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Devuelve el nombre del elemento que identifica un `IScriptEntry` objeto.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Para las entradas que representan un único objeto (por ejemplo, una función), devuelve el nombre del objeto.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Devuelve la posición de inicio y la longitud de una entrada.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Devuelve información de tipo para un `IScriptEntry` objeto de función.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Devuelve el texto que se corresponde con un `IScriptEntry` bloque de scripts o el código fuente que se encuentra en un `IScriptScriptlet` controlador de eventos.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Establece el texto que se encuentra en el cuerpo de un `IScriptEntry` bloque de script o un `IScriptScriptlet` scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Establece el nombre del elemento que identifica un `IScriptEntry` objeto.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Para las entradas que representan un único objeto (por ejemplo, una función), Establece el nombre del objeto.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Conjuntos de información de tipo para un `IScriptEntry` objeto de función.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Establece el texto que se corresponde con un `IScriptEntry` bloque de scripts o el código fuente que se encuentra en un `IScriptScriptlet` controlador de eventos.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Authoring (Interfaces)](../../winscript/reference/active-script-authoring-interfaces.md)