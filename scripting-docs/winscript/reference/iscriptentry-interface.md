---
title: IScriptEntry (interfaz) | Documentos de Microsoft
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
ms.openlocfilehash: 0dc50a6aa5cf032827feac6b483b141b79f60e77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787729"
---
# <a name="iscriptentry-interface"></a>IScriptEntry (Interfaz)
Un objeto que implementa el `IScriptEntry` interfaz representa un bloque de script o un objeto de función.  
  
 Además de los métodos heredados de `IScriptNode`, el `IScriptEntry` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Devuelve el texto que corresponde al cuerpo de un `IScriptEntry` scriptlet, bloque de función o bloque de script.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Devuelve el nombre del elemento que identifica un `IScriptEntry` objeto.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Para las entradas que representan un único objeto (por ejemplo, una función), devuelve el nombre del objeto.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Devuelve la posición inicial y longitud de una entrada.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Devuelve información de tipo para un `IScriptEntry` objeto de función.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Devuelve el texto que se corresponde con un `IScriptEntry` bloque de script o el código fuente que se encuentra en un `IScriptScriptlet` controlador de eventos.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Establece el texto que se encuentra en el cuerpo de un `IScriptEntry` bloque de script o un `IScriptScriptlet` scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Establece el nombre del elemento que identifica un `IScriptEntry` objeto.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Para las entradas que representan un único objeto (por ejemplo, una función), Establece el nombre del objeto.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Conjuntos de información de tipo para un `IScriptEntry` objeto de función.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Establece el texto que se corresponde con un `IScriptEntry` bloque de script o el código fuente que se encuentra en un `IScriptScriptlet` controlador de eventos.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Authoring (Interfaces)](../../winscript/reference/active-script-authoring-interfaces.md)