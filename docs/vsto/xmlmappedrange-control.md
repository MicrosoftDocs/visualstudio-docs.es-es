---
title: XmlMappedRange (control)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0ee0bc8b74c9a9006c9ac0a59d95da5708e62489
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597899"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange (control)
  El <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control es un intervalo que se crea solo cuando un elemento de esquema no es de repetición se asigna a una celda en Microsoft Office Excel. Por ejemplo, cuando el `maxOccurs` atributo de un elemento de esquema es igual a 1. Después de que Visual Studio crea el intervalo XML asignado, puede programar con él directamente sin tener que recorrer el modelo de objetos de Excel. Solo se puede eliminar un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control dentro de Excel cuando se quita la asignación de elemento.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: ¿Usar la asignación de XML en Excel? ](http://go.microsoft.com/fwlink/?LinkID=130288).

## <a name="bind-data-to-the-control"></a>Enlazar datos al control
 Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control admite el enlace a un único campo de datos (enlace de datos simple). El <xref:Microsoft.Office.Tools.Excel.ListObject> can control admite el enlace de datos complejos y se crea automáticamente cuando se asigna un elemento de esquema repetitivo a una celda. Para obtener más información, consulte [control ListObject](../vsto/listobject-control.md).

 El <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> está enlazado a un origen de datos mediante el <xref:System.Windows.Forms.Control.DataBindings%2A> propiedad. Cuando un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se agrega a una celda de la hoja de cálculo, Visual Studio genera un conjunto de datos de los datos en las celdas asignadas automáticamente y se enlaza el control a ese conjunto de datos. La propiedad de enlace de datos de forma predeterminada el <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> es <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.

 Si los datos en el conjunto de datos enlazado se actualizan mediante cualquier mecanismo, el <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control refleja los cambios.

## <a name="formatting"></a>Formato
 Puede aplicar el mismo formato a un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control que se puede aplicar a un <xref:Microsoft.Office.Interop.Excel.Range>. Esto incluye bordes, fuentes, formato de número y estilos.

## <a name="events"></a>Eventos
 Los eventos disponibles para el <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control son:

-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

-   <xref:System.ComponentModel.Component.Disposed>

-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Vea también
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Cómo: Agregar controles XMLMappedRange a hojas de cálculo](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
