---
title: Lista de objetos de la ventana Propiedades | Microsoft Docs
description: Obtenga información sobre las interfaces que se usan para interactuar con la lista de objetos ventana Propiedades en el IDE Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 908acf3f8ecad390266c3d085778dc13077a6fa8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903442"
---
# <a name="properties-window-object-list"></a>Lista de objetos de la ventana Propiedades
La lista de objetos de la **ventana** Propiedades es una lista desplegable que permite cambiar la selección a otros objetos disponibles dentro de una o varias ventanas seleccionadas. Al seleccionar un objeto diferente desde esta lista, se desencadena una llamada a para informar al entorno de que se ha seleccionado <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> un nuevo objeto. A continuación, se cambia la **información** que se muestra en la ventana Propiedades para mostrar las propiedades asociadas al objeto recién seleccionado.

## <a name="the-object-list"></a>Lista de objetos
 La lista de objetos consta de dos campos: el nombre del objeto (que se muestra en negrita) y el tipo de objeto.

 El nombre del objeto mostrado a la izquierda del tipo de objeto en negrita se recupera del propio objeto mediante la `Name` propiedad proporcionada por la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> . <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, el único método de <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , devuelve para la <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> coclase de esa interfaz. La **ventana** Propiedades usa para obtener el nombre de la coclase, que se muestra como el nombre del objeto <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> en la lista desplegable.

 Si el objeto no tiene una propiedad , no se muestra un nombre en el `Name` área Nombre de la lista de objetos. Puede agregar una propiedad Name al objeto si desea que el nombre se muestre en la lista de objetos.

 Si el objeto COM no implementa , la ventana Propiedades muestra el nombre de la interfaz en lugar del nombre del objeto en el <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> lado izquierdo de la lista. 

## <a name="see-also"></a>Consulta también
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
