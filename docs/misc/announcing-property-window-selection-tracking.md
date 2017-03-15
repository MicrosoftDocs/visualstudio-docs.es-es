---
title: "Anuncio del seguimiento de selecci&#243;n de la ventana de propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], compatibilidad con páginas de propiedades"
  - "páginas de propiedades, selección de seguimiento"
  - "ventana de propiedades, selección de seguimiento"
  - "selección, seguimiento"
  - "editores [Visual Studio SDK], compatibilidad con la ventana Propiedades"
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Anuncio del seguimiento de selecci&#243;n de la ventana de propiedades
Si desea ejecutar la ventana de **Propiedades** o las páginas de **Propiedad** , por ejemplo, un formulario, texto, o una selección para el que desea ver propiedades, debe haber completado conocimiento de cómo se coordina la selección.  Por ejemplo, debe saber si tiene la selección única o selecciones múltiples.  Se necesita entonces anunciar el tipo de selección \(uno o varios\) al IDE mediante la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  Esta interfaz proporciona la información necesaria para la ventana de **Propiedades** .  
  
### Para anunciar la selección al entorno  
  
1.  llamada `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>.  
  
    1.  Para ello, utilice el puntero de sitio pasado a la vista cuando se creó.  
  
    2.  Llame a `QueryService` de vista para el servicio de `SID_STrackSelection` .  
  
         esto devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> cada vez que cambia la selección, y pase un puntero a un objeto que implementa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
     El objeto contenedor de selección puede usar pick o las selecciones múltiples y contiene información de selección en un objeto de `IDispatch` .  Llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> notifica a la ventana de **Propiedades** que la selección ha cambiado.  La ventana de **Propiedades** utilice los objetos de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para determinar si es único o las selecciones múltiples han producido, y cuáles son las selecciones reales del objeto.  
  
     Si especifica una selección múltiple, la ventana de **Propiedades** busca la intersección entre las propiedades comunes para los objetos.  Si especifica una sola selección de objeto, en la ventana de **Propiedades** muestra todas las propiedades del objeto.  
  
## Vea también  
 [Extender propiedades](../extensibility/internals/extending-properties.md)   
 [Páginas de propiedades](../extensibility/internals/property-pages.md)