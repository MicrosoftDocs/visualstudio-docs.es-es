---
title: Lista de objetos de ventana de propiedades | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6b7d238f7ce64122ac18a52dab59afb063ce47e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="properties-window-object-list"></a>Lista de objetos de ventana de propiedades
La lista de objetos en el **propiedades** ventana es una lista desplegable que le permite cambiar la selección a otros objetos disponibles dentro de una o varias ventanas seleccionados. Al seleccionar un objeto diferente desde esta lista desencadena una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> para informar el entorno que se ha seleccionado un nuevo objeto. La información mostrada en el **propiedades** ventana, a continuación, se cambia para mostrar las propiedades asociadas con el objeto recién seleccionado.  
  
## <a name="the-object-list"></a>La lista de objetos  
 La lista de objetos consta de dos campos: el nombre de objeto (que se muestra en negrita) y el tipo de objeto.  
  
 El nombre del objeto aparece a la izquierda del tipo de objeto en negrita se recupera desde el propio objeto mediante la `Name` propiedad proporcionada por el <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interfaz. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, el único método en <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, devuelve <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> para coclase de esa interfaz. El **propiedades** ventana usa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> para obtener el nombre de la coclase, que se muestra como el nombre del objeto en la lista desplegable.  
  
 Si el objeto no tiene un `Name` propiedad, un nombre no se muestra en el área de nombre de la lista de objetos. Puede agregar una propiedad de nombre para el objeto si desea que el nombre mostrado en la lista de objetos.  
  
 Si el objeto COM no implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **propiedades** ventana muestra el nombre de la interfaz en lugar del nombre de objeto en el lado izquierdo de la lista.  
  
## <a name="see-also"></a>Vea también  
 [Extensión de propiedades](../../extensibility/internals/extending-properties.md)