---
title: Información general del modelo de objetos de Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f7f15cc3ce8396e4cd10a49a1427f1ba1be76b50
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
---
# <a name="excel-object-model-overview"></a>Información general sobre el modelo de objetos de Excel
  Para desarrollar soluciones que usen Microsoft Office Excel, puede interactuar con los objetos proporcionados por el modelo de objetos de Excel. Este tema presenta los objetos más importantes:  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 El modelo de objetos está estrechamente relacionado con la interfaz de usuario. El objeto <xref:Microsoft.Office.Interop.Excel.Application> representa toda la aplicación, y cada objeto <xref:Microsoft.Office.Interop.Excel.Workbook> contiene una colección de objetos `Worksheet`. A partir de ahí, la principal abstracción que representa celdas es el objeto <xref:Microsoft.Office.Interop.Excel.Range>, que permite trabajar con celdas individuales o grupos de celdas.  
  
 Además del modelo de objetos de Excel, los proyectos de Office en Visual Studio proporcionan *elementos host* y *controles host* que extienden algunos objetos en el modelo de objetos de Excel. Los elementos y controles host se comportan como los objetos de Excel que extienden, pero tienen también una funcionalidad adicional, como capacidades de enlace de datos y eventos adicionales. Para obtener más información, consulte [automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md) y [elementos Host y hospedar información general sobre controles](../vsto/host-items-and-host-controls-overview.md).  
  
 En este tema se proporciona una breve introducción del modelo de objetos de Excel. Para obtener recursos donde puede obtener más información sobre el modelo de objetos de Excel completo, vea [usar la documentación del modelo de objetos de Excel](#ExcelOMDocumentation).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [¿cómo controladores de eventos de uso de I: en un complemento 2007 de Excel?](http://go.microsoft.com/fwlink/?LinkID=130291), y [¿cómo I: usar las formas para crear un gráfico de burbujas ¿en Excel? ](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## <a name="access-objects-in-an-excel-project"></a>Obtener acceso a objetos en un proyecto de Excel  
 Cuando se crea un nuevo proyecto de complemento de VSTO para Excel, Visual Studio crea automáticamente un *ThisAddIn.vb* o *ThisAddIn.cs* archivo de código. Puede obtener acceso al objeto Application mediante `Me.Application` o `this.Application`.  
  
 Cuando se crea un nuevo proyecto de nivel de documento para Excel, tiene la opción de crear un nuevo proyecto de libro de Excel o plantilla de Excel. Visual Studio crea automáticamente los siguientes archivos de código en los nuevos proyectos de Excel, tanto de libro como de plantilla.  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 Puede utilizar la clase `Globals` en el proyecto para tener acceso a `ThisWorkbook`, `Sheet1`, `Sheet2` o `Sheet3` desde fuera de la clase correspondiente. Para obtener más información, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md). El ejemplo siguiente se llama el <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> método de `Sheet1` , independientemente de si el código se coloca en uno de los `Sheet` *n* clases o el `ThisWorkbook` clase.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Puesto que los datos de un documento de Excel están muy estructurados, el modelo de objetos es jerárquico y sencillo. Excel proporciona cientos de objetos con los que quizás desee interactuar, pero puede empezar a trabajar en el modelo de objetos centrándose en un subconjunto muy pequeño de los objetos disponibles. Entre estos objetos están los cuatro siguientes:  
  
-   Application  
  
-   Libro  
  
-   Hoja de cálculo  
  
-   Intervalo  
  
 Gran parte del trabajo realizado con Excel se centra en estos cuatro objetos y sus miembros.  
  
### <a name="application-object"></a>Application (objeto)  
 El objeto <xref:Microsoft.Office.Interop.Excel.Application> de Excel representa la propia aplicación Excel. El objeto <xref:Microsoft.Office.Interop.Excel.Application> expone una gran cantidad de información acerca de la aplicación en ejecución, las opciones que se aplican a esa instancia y los objetos del usuario actual que se abren en la instancia.  
  
> [!NOTE]  
>  No debería establecer el <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> propiedad de la <xref:Microsoft.Office.Interop.Excel.Application> objeto en Excel para **false**. Al establecer esta propiedad como false, impide que Excel active cualquier evento, incluidos los eventos de los controles host.  
  
### <a name="workbook-object"></a>Objeto Workbook  
 El objeto <xref:Microsoft.Office.Interop.Excel.Workbook> representa un único libro dentro de la aplicación Excel.  
  
 Las herramientas de desarrollo de Office en Visual Studio extienden el objeto <xref:Microsoft.Office.Interop.Excel.Workbook> proporcionando el tipo <xref:Microsoft.Office.Tools.Excel.Workbook>. Este tipo da acceso a todas las características de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook>. Para obtener más información, consulte [elemento host Workbook](../vsto/workbook-host-item.md).  
  
### <a name="worksheet-object"></a>Worksheet (objeto)  
 El objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> es miembro de la colección <xref:Microsoft.Office.Interop.Excel.Worksheets>. Muchas de las propiedades, métodos y eventos de <xref:Microsoft.Office.Interop.Excel.Worksheet> son idénticos o similares a los miembros proporcionados por los objetos <xref:Microsoft.Office.Interop.Excel.Application> o <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Excel proporciona una colección <xref:Microsoft.Office.Interop.Excel.Sheets> como propiedad de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook>. Cada miembro de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> es un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Las herramientas de desarrollo de Office en Visual Studio extienden el objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> proporcionando el tipo <xref:Microsoft.Office.Tools.Excel.Worksheet>. Este tipo da acceso a todas las características de un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> y a nuevas características como la capacidad de hospedar controles administrados y de controlar nuevos eventos. Para obtener más información, consulte [elemento host Worksheet](../vsto/worksheet-host-item.md).  
  
### <a name="range-object"></a>Range (objeto)  
 El objeto <xref:Microsoft.Office.Interop.Excel.Range> es el objeto que más utilizará en las aplicaciones de Excel. Para poder manipular una región de Excel, debe expresarla como un objeto <xref:Microsoft.Office.Interop.Excel.Range> y trabajar con métodos y propiedades de ese intervalo. Un objeto <xref:Microsoft.Office.Interop.Excel.Range> representa una celda, una fila, una columna, una selección de celdas que contiene uno o más bloques de celdas (que podrían o no ser contiguas) o incluso un grupo de celdas de varias hojas.  
  
 Visual Studio extiende el objeto <xref:Microsoft.Office.Interop.Excel.Range> proporcionando los tipos <xref:Microsoft.Office.Tools.Excel.NamedRange> y <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Estos tipos tienen la mayoría de las características de un objeto <xref:Microsoft.Office.Interop.Excel.Range>, además de nuevas características como la capacidad de enlace de datos y nuevos eventos. Para obtener más información, consulte [control NamedRange](../vsto/namedrange-control.md) y [XmlMappedRange (control)](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Usar la documentación del modelo de objetos de Excel  
 Para obtener información completa sobre el modelo de objetos de Excel, puede consultar la referencia del ensamblado de interoperabilidad primario (PIA) de Excel y la referencia del modelo de objetos VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Referencia de ensamblado de interoperabilidad primario  
 La documentación de referencia de los PIA de Excel describe los tipos Del ensamblado de interoperabilidad primario para Excel. Esta documentación está disponible en la siguiente ubicación: [referencia de ensamblado de interoperabilidad primario de Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 Para obtener más información sobre el diseño de los PIA de Excel, como las diferencias entre las clases e interfaces en el PIA y cómo se implementan los eventos en los PIA, consulte [información general de las clases e interfaces de los ensamblados de interoperabilidad primariosdeOffice](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>Referencia del modelo de objetos VBA  
 La referencia del modelo de objetos de VBA documenta el modelo de objetos de Excel tal como se expone al código de Visual Basic para Aplicaciones (VBA). Para obtener más información, consulte [referencia del modelo de objetos de Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del PIA de Excel. Por ejemplo, el objeto de hoja de cálculo en la referencia del modelo de objetos VBA corresponde a la <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto en los PIA de Excel. Aunque la referencia del modelo de objetos VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe traducir el código VBA de esta referencia a Visual Basic o Visual C# si quiere usarlo en un proyecto de Excel creado con Visual Studio.  
  
### <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Soluciones de Excel](../vsto/excel-solutions.md)|Explica cómo crear personalizaciones de nivel de documento y complementos de VSTO para Microsoft Office Excel.|  
|[Trabajar con rangos](../vsto/working-with-ranges.md)|Proporciona ejemplos que muestran cómo realizar tareas habituales con rangos.|  
|[Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)|Proporciona ejemplos que muestran cómo realizar tareas habituales con hojas de cálculo.|  
|[Trabajar con libros](../vsto/working-with-workbooks.md)|Proporciona ejemplos que muestran cómo realizar tareas habituales con libros.|  
  
  