---
title: "IDebugDocumentText2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2"
helpviewer_keywords: 
  - "Interfaz IDebugDocumentText2"
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa un documento de texto.  
  
## Sintaxis  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## Notas para los implementadores  
 Un motor de depuración \(DE\) implementa esta interfaz cuando el código fuente que necesita proporcionar está en formato de texto.  Puesto que éste es el caso más típico, si un OF implementa la interfaz de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , también debe implementar la interfaz de `IDebugDocumentText2` .  
  
## Notas para los llamadores  
 utilice el método de `QueryInterface` para obtener esta interfaz de una interfaz de `IDebugDocument2` .  
  
## métodos en el orden de Vtable  
 Además de los métodos de la interfaz de `IDebugDocument2` , esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera el tamaño del texto en esta posición en el documento.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|recupera el texto de la posición especificada en el documento.|  
  
## Comentarios  
 Un objeto que implementa esta interfaz también debe implementar la interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> , que proporciona la interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> para un objeto de [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)