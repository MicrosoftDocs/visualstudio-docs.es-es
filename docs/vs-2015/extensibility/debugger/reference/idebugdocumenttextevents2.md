---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b574ae45dafed11ed28047859676524054951512
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65678967"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz se utiliza para notificar a Visual Studio los cambios realizados en el documento de origen que proporciona el motor de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El DE implementa esta interfaz para admitir la realización de cambios en el código fuente. Esta interfaz se implementa normalmente en el mismo objeto que implementa la interfaz [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] obtiene esta interfaz a través de una llamada al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método. La <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz se obtiene de una llamada al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> método. La <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz se obtiene llamando al método [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en una interfaz [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDebugDocumentTextEvents2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[Destruir](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica que se ha destruido todo el documento.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica al paquete de depuración que se ha insertado texto en el documento.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica al paquete de depuración que se ha quitado el texto del documento.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica al paquete de depuración que el texto se ha reemplazado en el documento.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica al paquete de depuración que se han actualizado los atributos de texto en el documento.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al receptor el evento de que se han actualizado los atributos del documento.|  
  
## <a name="remarks"></a>Observaciones  
 Solo los motores de depuración que proporcionan sus propios documentos aprovecharán la `IDebugDocumentTextEvent2` interfaz. Un ejemplo de esto sería un motor de depuración de scripting. En el proceso de interpretar los scripts, se puede generar código fuente nuevo que no está presente en ningún archivo de disco y solo lo conoce el DE.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
