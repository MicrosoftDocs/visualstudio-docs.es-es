---
title: IDebugDocumentTextEvents2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 242c15cc456c3a27ba7b7da45a11031b026c02d3
ms.lasthandoff: 04/05/2017

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
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Obtiene esta interfaz mediante una llamada a la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>método.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> El <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>interfaz se obtiene de una llamada a la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>método.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> </xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> El <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>interfaz se obtiene mediante una llamada a la [QueryInterface](/cpp/atl/queryinterface) método en un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>  
  
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
