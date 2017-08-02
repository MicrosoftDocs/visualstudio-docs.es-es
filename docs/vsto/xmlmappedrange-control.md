---
title: "XmlMappedRange (Control)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "XMLMappedRange (control)"
  - "XMLMappedRange (control), enlace de datos"
  - "XMLMappedRange (control), eventos"
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# XmlMappedRange (Control)
  El control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> es un rango que sólo se crea cuando un elemento de esquema que no es de repetición se asigna a una celda en Microsoft Office Excel.  Por ejemplo, cuando el atributo `maxOccurs` de un elemento de esquema es igual a 1.  Después de que Visual Studio crea el rango XML asignado, es posible programar directamente con él sin tener que recorrer el modelo de objetos de Excel.  Sólo puede eliminar un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> en Excel si se quita la asignación de elemento.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![vínculo a vídeo](~/docs/data-tools/media/playvideo.gif "vínculo a vídeo") Para obtener una demostración en vídeo relacionada, vea [How Do I: Use XML Mapping in Excel?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## Enlazar datos al control  
 Un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> admite el enlace a un campo de datos único \(enlace de datos simple\).  El control <xref:Microsoft.Office.Tools.Excel.ListObject> puede admitir enlaces de datos complejos y se crea automáticamente cuando se asigna a una celda un elemento de esquema de repetición.  Para obtener más información, vea [ListObject &#40;Control&#41;](../vsto/listobject-control.md).  
  
 El control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se enlaza a un origen de datos mediante la propiedad <xref:System.Windows.Forms.Control.DataBindings%2A>.  Cuando se agrega un objeto <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> a una celda de hoja de cálculo, Visual Studio genera automáticamente un conjunto de datos a partir de los datos de las celdas asignadas y enlaza el control a ese conjunto de datos.  La propiedad de enlace de datos predeterminada del control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> es <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Si los datos del conjunto de datos enlazado se actualizan mediante cualquier mecanismo, el control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> reflejará los cambios.  
  
## Formato  
 Puede aplicar el mismo formato a un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> que a <xref:Microsoft.Office.Interop.Excel.Range>.  Esto incluye bordes, fuentes, formato de número y estilos.  
  
## Eventos  
 Los eventos disponibles para el control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> son:  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## Vea también  
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Cómo: Agregar controles XMLMappedRange a hojas de cálculo](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  