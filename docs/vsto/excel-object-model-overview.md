---
title: "Informaci&#243;n general sobre el modelo de objetos de Excel"
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
  - "modelo de objetos de Excel"
  - "modelos de objeto [desarrollo de Office en Visual Studio], Excel"
  - "modelos de objeto [desarrollo de Office en Visual Studio], Office"
  - "objetos [desarrollo de Office en Visual Studio], modelos de objetos de Office"
  - "modelos de objetos de Office"
  - "Range (objeto)"
  - "Workbook (clase)"
  - "Worksheet (objeto)"
ms.assetid: e4b2e46b-ea6c-4a88-a416-a7d4f495fc33
caps.latest.revision: 66
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 65
---
# Informaci&#243;n general sobre el modelo de objetos de Excel
  Para desarrollar soluciones que usen Microsoft Office Excel, puede interactuar con los objetos proporcionados por el modelo de objetos de Excel.  Este tema presenta los objetos más importantes:  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 El modelo de objetos está estrechamente relacionado con la interfaz de usuario.  El objeto <xref:Microsoft.Office.Interop.Excel.Application> representa toda la aplicación, y cada objeto <xref:Microsoft.Office.Interop.Excel.Workbook> contiene una colección de objetos `Worksheet`.  A partir de ahí, la principal abstracción que representa celdas es el objeto <xref:Microsoft.Office.Interop.Excel.Range>, que permite trabajar con celdas individuales o grupos de celdas.  
  
 Además del modelo de objetos de Excel, los proyectos de Office en Visual Studio proporcionan *elementos host* y *controles host* que extienden algunos objetos del modelo de objetos de Excel.  Los elementos y controles host se comportan como los objetos de Excel que extienden, pero tienen también una funcionalidad adicional, como capacidades de enlace de datos y eventos adicionales.  Para obtener más información, vea [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md) e [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
 En este tema se proporciona una breve introducción del modelo de objetos de Excel.  Para conocer los recursos donde puede obtener más información sobre el modelo de objetos de Excel completo, vea [Usar la documentación del modelo de objetos de Excel](#ExcelOMDocumentation).  
  
 ![vínculo a vídeo](~/data-tools/media/playvideo.gif "vínculo a vídeo") Puede ver una demostración en vídeo relacionada en estas dos páginas sobre [cómo usar los controladores de eventos en un complemento de Excel 2007](http://go.microsoft.com/fwlink/?LinkID=130291) y [cómo usar las formas para crear un gráfico de burbujas en Excel](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## Acceso a los objetos de un proyecto de Excel  
 Cuando se crea un nuevo proyecto de complemento de VSTO para Excel, Visual Studio crea automáticamente un archivo de código ThisAddIn.vb o ThisAddIn.cs.  Puede obtener acceso al objeto Application mediante `Me.Application` o `this.Application`.  
  
 Cuando se crea un nuevo proyecto de nivel de documento para Excel, tiene la opción de crear un nuevo proyecto de libro de Excel o plantilla de Excel.  Visual Studio crea automáticamente los siguientes archivos de código en los nuevos proyectos de Excel, tanto de libro como de plantilla.  
  
|Visual Basic|C\#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 Puede utilizar la clase `Globals` en el proyecto para tener acceso a `ThisWorkbook`, `Sheet1`, `Sheet2` o `Sheet3` desde fuera de la clase correspondiente.  Para obtener más información, vea este artículo de [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  El ejemplo siguiente llama al método <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> de `Sheet1`, independientemente de si el código se coloca en una de las clases `Sheet`*n* o en la clase `ThisWorkbook`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#82)]  
  
 Puesto que los datos de un documento de Excel están muy estructurados, el modelo de objetos es jerárquico y sencillo.  Excel proporciona cientos de objetos con los que quizás desee interactuar, pero puede empezar a trabajar en el modelo de objetos centrándose en un subconjunto muy pequeño de los objetos disponibles.  Entre estos objetos están los cuatro siguientes:  
  
-   Administración de  
  
-   Libro  
  
-   Hoja de cálculo  
  
-   Intervalo  
  
 Gran parte del trabajo realizado con Excel se centra en estos cuatro objetos y sus miembros.  
  
### Objeto de aplicación  
 El objeto <xref:Microsoft.Office.Interop.Excel.Application> de Excel representa la propia aplicación Excel.  El objeto <xref:Microsoft.Office.Interop.Excel.Application> expone una gran cantidad de información acerca de la aplicación en ejecución, las opciones que se aplican a esa instancia y los objetos del usuario actual que se abren en la instancia.  
  
> [!NOTE]  
>  No debería establecer la propiedad <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> del objeto <xref:Microsoft.Office.Interop.Excel.Application> en Excel como **false**.  Al establecer esta propiedad como false, impide que Excel active cualquier evento, incluidos los eventos de los controles host.  
  
### Objeto Workbook  
 El objeto <xref:Microsoft.Office.Interop.Excel.Workbook> representa un único libro dentro de la aplicación Excel.  
  
 Las herramientas de desarrollo de Office en Visual Studio extienden el objeto <xref:Microsoft.Office.Interop.Excel.Workbook> proporcionando el tipo <xref:Microsoft.Office.Tools.Excel.Workbook>.  Este tipo da acceso a todas las características de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook>.  Para obtener más información, vea [Elemento host Workbook](../vsto/workbook-host-item.md).  
  
### Objeto Worksheet  
 El objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> es miembro de la colección <xref:Microsoft.Office.Interop.Excel.Worksheets>.  Muchas de las propiedades, métodos y eventos de <xref:Microsoft.Office.Interop.Excel.Worksheet> son idénticos o similares a los miembros proporcionados por los objetos <xref:Microsoft.Office.Interop.Excel.Application> o <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Excel proporciona una colección <xref:Microsoft.Office.Interop.Excel.Sheets> como propiedad de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook>.  Cada miembro de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> es un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Las herramientas de desarrollo de Office en Visual Studio extienden el objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> proporcionando el tipo <xref:Microsoft.Office.Tools.Excel.Worksheet>.  Este tipo da acceso a todas las características de un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> y a nuevas características como la capacidad de hospedar controles administrados y de controlar nuevos eventos.  Para obtener más información, vea [Elemento host Worksheet](../vsto/worksheet-host-item.md).  
  
### Objeto Range  
 El objeto <xref:Microsoft.Office.Interop.Excel.Range> es el objeto que más utilizará en las aplicaciones de Excel.  Para poder manipular una región de Excel, debe expresarla como un objeto <xref:Microsoft.Office.Interop.Excel.Range> y trabajar con métodos y propiedades de ese intervalo.  Un objeto <xref:Microsoft.Office.Interop.Excel.Range> representa una celda, una fila, una columna, una selección de celdas que contiene uno o más bloques de celdas \(que podrían o no ser contiguas\) o incluso un grupo de celdas de varias hojas.  
  
 Visual Studio extiende el objeto <xref:Microsoft.Office.Interop.Excel.Range> proporcionando los tipos <xref:Microsoft.Office.Tools.Excel.NamedRange> y <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>.  Estos tipos tienen la mayoría de las características de un objeto <xref:Microsoft.Office.Interop.Excel.Range>, además de nuevas características como la capacidad de enlace de datos y nuevos eventos.  Para obtener más información, consulte [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md) y [XmlMappedRange &#40;Control&#41;](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Usar la documentación del modelo de objetos de Excel  
 Para obtener información completa sobre el modelo de objetos de Excel, puede consultar la referencia del ensamblado de interoperabilidad primario \(PIA\) de Excel y la referencia del modelo de objetos VBA.  
  
### Referencia de ensamblado de interoperabilidad primario  
 La documentación de referencia de los PIA de Excel describe los tipos Del ensamblado de interoperabilidad primario para Excel.  Esta documentación está disponible en la siguiente ubicación: [Referencia de ensamblado de interoperabilidad primario de Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 Para obtener más información sobre el diseño de los PIA de Excel, como las diferencias entre las clases y las interfaces en el PIA y cómo se implementan los eventos en los PIA, vea [Información general sobre las clases y las interfaces de los ensamblados de interoperabilidad primarios de Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### Referencia del modelo de objetos de VBA  
 La referencia del modelo de objetos de VBA documenta el modelo de objetos de Excel tal como se expone al código de Visual Basic para Aplicaciones \(VBA\).  Para obtener más información, vea [Referencia del modelo de objetos \(referencia para desarrolladores de Excel 2013\)](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del PIA de Excel.  Por ejemplo, el objeto Worksheet en la referencia del modelo de objetos VBA corresponde al objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> del PIA de Excel.  Aunque la referencia del modelo de objetos VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe traducir el código VBA de esta referencia a Visual Basic o Visual C\# si quiere usarlo en un proyecto de Excel creado con Visual Studio.  
  
### Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Soluciones de Excel](../vsto/excel-solutions.md)|Explica cómo crear personalizaciones de nivel de documento y complementos de VSTO para Microsoft Office Excel.|  
|[Trabajar con rangos](../vsto/working-with-ranges.md)|Proporciona ejemplos que muestran cómo realizar tareas habituales con rangos.|  
|[Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)|Proporciona ejemplos que muestran cómo realizar tareas habituales con hojas de cálculo.|  
|[Trabajar con libros](../vsto/working-with-workbooks.md)|Proporciona ejemplos que muestran cómo realizar tareas habituales con libros.|  
  
  