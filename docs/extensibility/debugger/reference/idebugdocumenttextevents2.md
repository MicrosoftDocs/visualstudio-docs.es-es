---
title: IDebugDocumentTextEvents2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f34bb09847659fdfc1dfcbd036aef2a47c8bd5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107675"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Esta interfaz se utiliza para notificar a Visual Studio sobre los cambios en el documento de origen que proporcionan el motor de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para admitir realizar los cambios en el código fuente. Esta interfaz se implementa normalmente en el mismo objeto que implementa el [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Obtiene esta interfaz mediante una llamada a la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método. El <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz se obtiene de una llamada a la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> método. El <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz se obtiene mediante una llamada a la [QueryInterface](/cpp/atl/queryinterface) método en un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugDocumentTextEvents2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica que se ha destruido todo el documento.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica que el paquete de depuración que se ha insertado el texto en el documento.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica que el paquete de depuración que se ha quitado el texto del documento.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica que el paquete de depuración que se ha reemplazado el texto en el documento.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica que el paquete de depuración que se han actualizado los atributos de texto en el documento.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al receptor del evento que se han actualizado los atributos del documento.|  
  
## <a name="remarks"></a>Comentarios  
 Solo los motores de depuración que proporcionan sus propios documentos podrían aprovechar las ventajas de la `IDebugDocumentTextEvent2` interfaz. Un ejemplo de esto sería un motor de depuración de secuencias de comandos. En el proceso de interpretación de secuencias de comandos, se puede generar nuevo código de origen que no está presente en cualquier archivo de disco y solo lo conoce el Alemania.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)