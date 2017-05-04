---
title: "IDebugDocumentText (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentText (interfaz)"
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText (Interfaz)
Proporciona acceso a una versión de texto \- sólo de depuración.  Esta interfaz utiliza convenciones siguientes:  
  
-   Las posiciones de caracteres y los números de línea son cero basado.  
  
-   Las posiciones de caracteres representan desplazamientos de caracteres; no representan desplazamientos de bytes o word.  Para Win32, una posición de caracteres es Unicode compensó.  
  
 Además de los métodos heredados de `IDebugDocument`, la interfaz `IDebugDocumentText` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Devuelve los atributos del documento.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Devuelve el número de líneas y de número de caracteres del documento.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Devuelve la posición del carácter correspondiente al primer carácter de una línea.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Devuelve el número de línea y, opcionalmente, el desplazamiento del carácter en la línea que corresponde a la posición de caracteres determinada.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Recupera los caracteres o los atributos de caracteres asociados a un intervalo de la posición.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Devuelve el intervalo de la posición del carácter correspondiente a un contexto del documento.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Crea un objeto de contexto del documento correspondiente al intervalo proporcionado de la posición.|