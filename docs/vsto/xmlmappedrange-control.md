---
title: Control XmlMappedRange (
description: Obtenga información sobre que el control XmlMappedRange (es un intervalo que solo se crea cuando se asigna un elemento de esquema que no es de repetición a una celda de Microsoft Excel.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f3b3fd140787d44cdd8364ce77d5292dfcd83f54
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525891"
---
# <a name="xmlmappedrange-control"></a>Control XmlMappedRange (
  El <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control es un intervalo que solo se crea cuando se asigna un elemento de esquema que no es de repetición a una celda de Microsoft Office Excel. Por ejemplo, cuando el `maxOccurs` atributo de un elemento de esquema es igual a 1. Después de que Visual Studio cree el intervalo asignado XML, puede programar directamente sin tener que recorrer el modelo de objetos de Excel. Solo se puede eliminar un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control dentro de Excel cuando se quita la asignación del elemento.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Enlazar datos al control
 Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control admite el enlace a un único campo de datos (enlace de datos simple). El <xref:Microsoft.Office.Tools.Excel.ListObject> control puede admitir el enlace de datos complejo y se crea automáticamente cuando se asigna un elemento de esquema repetido a una celda. Para obtener más información, vea [ListObject (control](../vsto/listobject-control.md)).

 El <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control se enlaza a un origen de datos mediante la <xref:System.Windows.Forms.Control.DataBindings%2A> propiedad. Cuando <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se agrega un a una celda de una hoja de cálculo, Visual Studio genera automáticamente un conjunto de datos a partir de los datos de las celdas asignadas y enlaza el control al conjunto de datos. La propiedad de enlace de datos predeterminada de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> es <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> .

 Si los datos del conjunto de datos enlazado se actualizan mediante cualquier mecanismo, el <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control reflejará los cambios.

## <a name="formatting"></a>Aplicación de formato
 Puede aplicar el mismo formato a un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control que puede aplicar a un <xref:Microsoft.Office.Interop.Excel.Range> . Esto incluye bordes, fuentes, formato de número y estilos.

## <a name="events"></a>Eventos
 Los eventos disponibles para el <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control son los siguientes:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Consulte también
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Cómo: agregar controles XmlMappedRange (a hojas de cálculo](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Cómo: asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
