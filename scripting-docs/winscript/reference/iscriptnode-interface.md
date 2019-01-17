---
title: IScriptNode (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8897d783f8a101b41dd7263061604fb1d82ec56
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344621"
---
# <a name="iscriptnode-interface"></a>IScriptNode (Interfaz)
Un objeto que implementa el `IScriptNode` interfaz representa una página Web.  
  
 Además de los métodos heredados de `IUnknown`, el `IScriptNode` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indica si un objeto aún está activo.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Agrega una instancia secundaria de `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Agrega un scriptlet como una instancia secundaria de un `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Elimina el árbol de objetos.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Devuelve al elemento secundario que está en el índice especificado en el nodo.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Devuelve un valor definido por la aplicación que se usa para asociar un scriptlet con el objeto host.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Devuelve el índice de un objeto en la lista de nodos secundarios del elemento primario.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Devuelve el lenguaje de scripting que utiliza el actual nodo de secuencia de comandos.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Devuelve el número de nodos secundarios de la `IScriptNode` objeto.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Devuelve el `IScriptNode` objeto que es el elemento primario de un objeto.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Authoring (Interfaces)](../../winscript/reference/active-script-authoring-interfaces.md)