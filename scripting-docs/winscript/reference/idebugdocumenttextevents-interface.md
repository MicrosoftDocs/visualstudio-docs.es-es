---
title: IDebugDocumentTextEvents (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bec89ae81d79fb7b0d822cafe2bf44f0ecd8ad81
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345666"
---
# <a name="idebugdocumenttextevents-interface"></a>IDebugDocumentTextEvents (Interfaz)
Proporciona eventos que indican los cambios realizados en el documento de texto asociado.  
  
> [!NOTE]
>  El texto del documento cambia cuando los eventos en esta interfaz de incendios. Controladores de eventos pueden recuperar el texto nuevo mediante el `IDebugDocumentText` interfaz.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugDocumentTextEvents` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Indica que el documento subyacente se ha destruido y ya no es válido|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Indica que se ha agregado el nuevo texto al documento|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Indica que se ha quitado el texto del documento.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Indica que se ha reemplazado el texto.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Indica que los atributos de texto asociados al intervalo de posición de carácter subyacente han cambiado.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Indica que se cambian los atributos del documento.|