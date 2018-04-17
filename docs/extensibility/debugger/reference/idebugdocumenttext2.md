---
title: IDebugDocumentText2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e0dc8344e19f422e65439aae6bafe12e3f62bee4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Esta interfaz representa un documento de texto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un motor de depuración (Alemania) implementa esta interfaz cuando el código fuente que debe proporcionar está en formato de texto. Puesto que este es el caso más habitual, si implementa un Alemania la [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz, esta debería implementar también el `IDebugDocumentText2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Use la `QueryInterface` método para obtener esta interfaz desde un `IDebugDocument2` interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el `IDebugDocument2` interfaz, esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera el tamaño del texto en esta posición en el documento.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera el texto de la posición especificada en el documento.|  
  
## <a name="remarks"></a>Comentarios  
 Un objeto que implementa esta interfaz también debe implementar la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> de la interfaz, que proporciona el <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz para un [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) objeto.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)