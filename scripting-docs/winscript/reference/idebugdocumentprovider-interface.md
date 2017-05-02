---
title: "IDebugDocumentProvider (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentProvider (interfaz)"
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider (Interfaz)
Proporciona los medios para crear instancias de un documento a petición.  
  
## Comentarios  
 Este multimedia indirectos para crear instancias de un documento:  
  
-   Permite que el documento cargue cuando es necesario.  
  
-   Permite que el objeto documento es contenido dentro del depurador el IDE.  
  
-   Permite varias maneras de tener acceso al mismo objeto de documento.  
  
 Esto separa eficazmente el documento del proveedor y permite al proveedor mantenga el tiempo de ejecución adicional, información de contexto.  
  
 Además de los métodos heredados de `IDebugDocumentInfo`, la interfaz `IDebugDocumentProvider` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Hace que el documento que se va a crear instancias si no existe.|