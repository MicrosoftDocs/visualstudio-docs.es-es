---
title: Lista de objetos de la ventana Propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95ef509491e05daf575e211ae479c815994eb3d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148328"
---
# <a name="properties-window-object-list"></a>Lista de objetos de la ventana Propiedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La lista de objetos de la ventana **propiedades** es una lista desplegable que permite cambiar la selección a otros objetos disponibles en una o varias ventanas seleccionadas. Al seleccionar un objeto diferente en esta lista, se desencadena una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> para informar al entorno de que se ha seleccionado un nuevo objeto. La información que se muestra en la ventana **propiedades** se cambia para mostrar las propiedades asociadas al objeto recién seleccionado.  
  
## <a name="the-object-list"></a>La lista de objetos  
 La lista de objetos consta de dos campos: el nombre del objeto (que se muestra en negrita) y el tipo de objeto.  
  
 El nombre de objeto que se muestra a la izquierda del tipo de objeto en negrita se recupera del propio objeto mediante la `Name` propiedad proporcionada por la <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interfaz. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, el único método en <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , devuelve <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> para la coclase de la interfaz. La ventana **propiedades** utiliza <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> para obtener el nombre de la coclase, que se muestra como el nombre de objeto en la lista desplegable.  
  
 Si el objeto no tiene una `Name` propiedad, no se muestra ningún nombre en el área de nombre de la lista de objetos. Puede Agregar una propiedad de nombre al objeto si desea que el nombre se muestre en la lista de objetos.  
  
 Si el objeto COM no implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , la ventana **propiedades** muestra el nombre de la interfaz en lugar del nombre de objeto en el lado izquierdo de la lista.  
  
## <a name="see-also"></a>Consulte también  
 [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
