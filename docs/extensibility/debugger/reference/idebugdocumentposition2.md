---
title: "IDebugDocumentPosition2 | Microsoft Docs"
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
  - "IDebugDocumentPosition2"
helpviewer_keywords: 
  - "Interfaz IDebugDocumentPosition2"
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa una posición abstracta en un archivo de código fuente.  
  
## Sintaxis  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## Notas para los implementadores  
 Visual Studio implementará normalmente esta interfaz.  Un motor de depuración \(DE\) también debería implementar esta interfaz si debe proporcionar su propio código fuente \(como cuando el OF implementa la interfaz de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) \).  
  
## Notas para los llamadores  
 Esta interfaz se pasa como argumento a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md).  También se proporciona como parte de una combinación de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) \(específicamente, una estructura de [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) \) que es a su vez parte de la estructura de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , que se utiliza para crear un punto de interrupción pendiente.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugDocumentPosition2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtiene el nombre del archivo de código fuente que contiene esta posición del documento.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|obtiene el documento que contiene.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina si esta posición se contiene en el documento especificado.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtiene el intervalo para esta posición del documento.|  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)