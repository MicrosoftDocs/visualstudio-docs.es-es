---
title: XmlMappedRange (Control) | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f4b78da11efafff45f34b3dc4ab9e7f1349a2e8a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange (Control)
  El <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control es un rango que sólo se crea cuando se asigna un elemento de esquema no repetitivo en una celda en Microsoft Office Excel. Por ejemplo, cuando el `maxOccurs` atributo de un elemento de esquema es igual a 1. Después de que Visual Studio crea el rango XML asignado, puede programar con ella directamente sin tener que recorrer el modelo de objetos de Excel. Sólo se puede eliminar un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control dentro de Excel cuando se quita la asignación de elemento.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [cómo hacer I: uso asignación XML en Excel?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## <a name="binding-data-to-the-control"></a>Enlazar datos al control  
 Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control admite el enlace a un campo de datos único (enlace de datos simple). El <xref:Microsoft.Office.Tools.Excel.ListObject> can control admite el enlace de datos complejo y se crea automáticamente cuando se asigna un elemento de esquema repetitivo a una celda. Para obtener más información, consulta [ListObject Control](../vsto/listobject-control.md).  
  
 El <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control se enlaza a un origen de datos mediante el <xref:System.Windows.Forms.Control.DataBindings%2A> propiedad. Cuando un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se agrega a una celda de la hoja de cálculo, Visual Studio genera automáticamente un conjunto de datos de los datos en las celdas asignadas y enlaza el control a ese conjunto de datos. La propiedad de enlace de datos predeterminada de la <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> es <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
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
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Cómo: agregar controles XMLMappedRange a hojas de cálculo](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cómo: asignar esquemas a hojas de cálculo dentro de Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  