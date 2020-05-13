---
title: Lista de objetos de la ventana Propiedades (Properties Window Object List) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706146"
---
# <a name="properties-window-object-list"></a>Lista de objetos de la ventana Propiedades
La lista de objetos de la ventana **Propiedades** es una lista desplegable que permite cambiar la selección a otros objetos disponibles en una o varias ventanas seleccionadas. Al seleccionar un objeto diferente de esta <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> lista, se desencadena una llamada para informar al entorno de que se ha seleccionado un nuevo objeto. A continuación, se cambia la información que se muestra en la ventana **Propiedades** para mostrar las propiedades asociadas al objeto recién seleccionado.

## <a name="the-object-list"></a>La lista de objetos
 La lista de objetos consta de dos campos: el nombre del objeto (que se muestra en negrita) y el tipo de objeto.

 El nombre de objeto que se muestra a la izquierda del tipo `Name` de objeto <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> en negrita se recupera del propio objeto mediante la propiedad proporcionada por la interfaz. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, el único <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>método <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> en , devuelve para la coclase de esa interfaz. La **Properties** ventana <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> Propiedades se utiliza para obtener el nombre de la coclase, que se muestra como el nombre del objeto en la lista desplegable.

 Si el objeto no `Name` tiene una propiedad, no se muestra un nombre en el área Nombre de la lista de objetos. Puede agregar una propiedad Name al objeto si desea que el nombre se muestre en la lista de objetos.

 Si el objeto COM <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>no implementa , la ventana **Propiedades** muestra el nombre de la interfaz en lugar del nombre del objeto en el lado izquierdo de la lista.

## <a name="see-also"></a>Vea también
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
