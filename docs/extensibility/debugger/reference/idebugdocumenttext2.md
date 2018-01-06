---
title: IDebugDocumentText2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentText2
helpviewer_keywords: IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c3540dc77821e6aa3fb3884d82cd0c83eee8e24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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