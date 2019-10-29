---
title: Control XmlMappedRange (
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
ms.openlocfilehash: 01417d9c08491edc882f7f758bb36e6184500e52
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985357"
---
# <a name="xmlmappedrange-control"></a>Control XmlMappedRange (
  El control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> es un intervalo que solo se crea cuando se asigna un elemento de esquema que no es de repetición a una celda de Microsoft Office Excel. Por ejemplo, cuando el `maxOccurs` atributo de un elemento de esquema es igual a 1. Después de que Visual Studio cree el intervalo asignado XML, puede programar directamente sin tener que recorrer el modelo de objetos de Excel. Solo se puede eliminar un control de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> en Excel cuando se quita la asignación del elemento.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Enlazar datos al control
 Un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> admite el enlace a un único campo de datos (enlace de datos simple). El control <xref:Microsoft.Office.Tools.Excel.ListObject> puede admitir el enlace de datos complejo y se crea automáticamente cuando se asigna un elemento de esquema repetido a una celda. Para obtener más información, vea [ListObject (control](../vsto/listobject-control.md)).

 El control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se enlaza a un origen de datos mediante la propiedad <xref:System.Windows.Forms.Control.DataBindings%2A>. Cuando se agrega una <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> a una celda de la hoja de cálculo, Visual Studio genera automáticamente un conjunto de datos a partir de los datos de las celdas asignadas y enlaza el control al conjunto de datos. La propiedad de enlace de datos predeterminada del <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> es <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.

 Si los datos del conjunto de datos enlazado se actualizan mediante cualquier mecanismo, el control de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> reflejará los cambios.

## <a name="formatting"></a>Formato
 Puede aplicar el mismo formato a un control de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> que puede aplicar a un <xref:Microsoft.Office.Interop.Excel.Range>. Esto incluye bordes, fuentes, formato de número y estilos.

## <a name="events"></a>Events
 Los eventos disponibles para el control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> son:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Vea también
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Cómo: agregar controles XmlMappedRange (a hojas de cálculo](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Cómo: asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
