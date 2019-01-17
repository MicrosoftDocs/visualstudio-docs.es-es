---
title: IDebugApplicationNode (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7bd38a0fbbdd596f6a1f6bb040190dddca78bf9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349002"
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode (Interfaz)
El `IDebugApplicationNode` interfaz extiende la funcionalidad de la `IDebugDocumentProvider` interfaz proporcionando un contexto dentro de un árbol de proyecto.  
  
 Además de los métodos heredados de `IDebugDocumentProvider`, el `IDebugApplicationNode` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Enumera los nodos secundarios de este nodo de la aplicación.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Devuelve el nodo primario de este nodo de la aplicación.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Establece el proveedor de documento para este nodo de la aplicación.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Hace que esta aplicación para liberar todas las referencias y entrar en un estado inactivo.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Este nodo de la aplicación se agrega al árbol del proyecto especificado.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Quita este nodo de la aplicación desde el árbol del proyecto.|