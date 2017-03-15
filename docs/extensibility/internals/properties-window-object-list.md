---
title: "Lista de objetos de ventana de propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ventana de propiedades, la lista de objetos"
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Lista de objetos de ventana de propiedades
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La lista de objeto en la ventana de **Propiedades** es una lista desplegable que permite cambiar la selección a otros objetos disponibles dentro de una o más ventanas seleccionado.  Seleccionar un objeto diferente dentro de esta lista desencadena una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> para informar al entorno que un nuevo objeto se ha seleccionado.  La información mostrada en la ventana de **Propiedades** se cambia para mostrar las propiedades asociadas con el objeto de seleccionado.  
  
## La lista de objetos  
 La lista de objeto consta de dos campos: el nombre de objeto \(presentado en negrita\) y el tipo de objeto.  
  
 El nombre de objeto producido a la izquierda del tipo de objeto en negrita se recupera del propio objeto mediante la propiedad de `Name` proporcionada por la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> .  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, el único método en <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, devuelve <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> de una coclase de esa interfaz.  La ventana de **Propiedades** utiliza <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> para obtener el nombre coclass, que se muestra como el nombre de objeto en la lista desplegable.  
  
 Si el objeto no tiene una propiedad de `Name` , un nombre no se muestra en el área de nombre de la lista de objetos.  Puede agregar una propiedad Name al objeto si desea que el nombre mostrado en la lista de objetos.  
  
 Si el objeto COM no implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, la ventana de **Propiedades** muestra el nombre de la interfaz en un nombre de objeto en el lado izquierdo de la lista.  
  
## Vea también  
 [Extender propiedades](../../extensibility/internals/extending-properties.md)