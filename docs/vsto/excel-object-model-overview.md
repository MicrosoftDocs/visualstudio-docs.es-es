---
title: Información general del modelo de objetos de Excel
description: Aprenda a interactuar con los objetos proporcionados por el modelo de objetos de Excel para desarrollar soluciones que usen Microsoft Office Excel.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a49dcc36d4079a6a945806b3112e3949ddcd79e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910292"
---
# <a name="excel-object-model-overview"></a>Información general del modelo de objetos de Excel
  Para desarrollar soluciones que usen Microsoft Office Excel, puede interactuar con los objetos proporcionados por el modelo de objetos de Excel. Este tema presenta los objetos más importantes:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  El modelo de objetos está estrechamente relacionado con la interfaz de usuario. El objeto <xref:Microsoft.Office.Interop.Excel.Application> representa toda la aplicación, y cada objeto <xref:Microsoft.Office.Interop.Excel.Workbook> contiene una colección de objetos `Worksheet`. A partir de ahí, la principal abstracción que representa celdas es el objeto <xref:Microsoft.Office.Interop.Excel.Range>, que permite trabajar con celdas individuales o grupos de celdas.

  Además del modelo de objetos de Excel, los proyectos de Office en Visual Studio proporcionan *elementos host* y *controles host* que extienden algunos objetos del modelo de objetos de Excel. Los elementos y controles host se comportan como los objetos de Excel que extienden, pero tienen también una funcionalidad adicional, como capacidades de enlace de datos y eventos adicionales. Para obtener más información, vea [automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md) y [información general sobre elementos y controles](../vsto/host-items-and-host-controls-overview.md)host.

  En este tema se proporciona una breve introducción del modelo de objetos de Excel. Para obtener más información sobre el modelo de objetos de Excel completo, vea [usar la documentación del modelo de objetos de Excel](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Obtener acceso a objetos en un proyecto de Excel
 Al crear un nuevo proyecto de complemento de VSTO para Excel, Visual Studio crea automáticamente un archivo de código *ThisAddIn. VB* o *ThisAddIn.CS* . Puede obtener acceso al objeto Application mediante `Me.Application` o `this.Application`.

 Cuando se crea un nuevo proyecto de nivel de documento para Excel, tiene la opción de crear un nuevo proyecto de libro de Excel o plantilla de Excel. Visual Studio crea automáticamente los siguientes archivos de código en los nuevos proyectos de Excel, tanto de libro como de plantilla.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sheet1.vb|Sheet1.cs|
|Sheet2.vb|Sheet2.cs|
|Sheet3.vb|Sheet3.cs|

 Puede utilizar la clase `Globals` en el proyecto para tener acceso a `ThisWorkbook`, `Sheet1`, `Sheet2` o `Sheet3` desde fuera de la clase correspondiente. Para obtener más información, consulte [acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md). En el ejemplo siguiente se llama al <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> método de `Sheet1` independientemente de si el código se coloca en una de las `Sheet` clases *n* o en la `ThisWorkbook` clase.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Puesto que los datos de un documento de Excel están muy estructurados, el modelo de objetos es jerárquico y sencillo. Excel proporciona centenares de objetos con los que es posible que desee interactuar, pero puede empezar a trabajar en el modelo de objetos centrándose en un pequeño subconjunto de los objetos disponibles. Entre estos objetos están los cuatro siguientes:

- Application

- Libro

- Hoja de cálculo

- Intervalo

  Gran parte del trabajo realizado con Excel se centra en estos cuatro objetos y sus miembros.

### <a name="application-object"></a>Objeto de aplicación
 El objeto <xref:Microsoft.Office.Interop.Excel.Application> de Excel representa la propia aplicación Excel. El objeto <xref:Microsoft.Office.Interop.Excel.Application> expone una gran cantidad de información acerca de la aplicación en ejecución, las opciones que se aplican a esa instancia y los objetos del usuario actual que se abren en la instancia.

> [!NOTE]
> No debería establecer la propiedad <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> del objeto <xref:Microsoft.Office.Interop.Excel.Application> en Excel como **false**. Al establecer esta propiedad como false, impide que Excel active cualquier evento, incluidos los eventos de los controles host.

### <a name="workbook-object"></a>Workbook (objeto)
 El objeto <xref:Microsoft.Office.Interop.Excel.Workbook> representa un único libro dentro de la aplicación Excel.

 Las herramientas de desarrollo de Office en Visual Studio extienden el objeto <xref:Microsoft.Office.Interop.Excel.Workbook> proporcionando el tipo <xref:Microsoft.Office.Tools.Excel.Workbook> . Este tipo da acceso a todas las características de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook>. Para obtener más información, vea [Workbook host Item](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Worksheet (objeto)
 El objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> es miembro de la colección <xref:Microsoft.Office.Interop.Excel.Worksheets>. Muchas de las propiedades, métodos y eventos de <xref:Microsoft.Office.Interop.Excel.Worksheet> son idénticos o similares a los miembros proporcionados por los objetos <xref:Microsoft.Office.Interop.Excel.Application> o <xref:Microsoft.Office.Interop.Excel.Workbook>.

 Excel proporciona una colección <xref:Microsoft.Office.Interop.Excel.Sheets> como propiedad de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook>. Cada miembro de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> es un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart>.

 Las herramientas de desarrollo de Office en Visual Studio extienden el objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> proporcionando el tipo <xref:Microsoft.Office.Tools.Excel.Worksheet> . Este tipo da acceso a todas las características de un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> y a nuevas características como la capacidad de hospedar controles administrados y de controlar nuevos eventos. Para obtener más información, vea [elemento host de hoja de cálculo](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Range (objeto)
 El objeto <xref:Microsoft.Office.Interop.Excel.Range> es el objeto que más utilizará en las aplicaciones de Excel. Para poder manipular una región de Excel, debe expresarla como un objeto <xref:Microsoft.Office.Interop.Excel.Range> y trabajar con métodos y propiedades de ese intervalo. Un objeto <xref:Microsoft.Office.Interop.Excel.Range> representa una celda, una fila, una columna, una selección de celdas que contiene uno o más bloques de celdas (que podrían o no ser contiguas) o incluso un grupo de celdas de varias hojas.

 Visual Studio extiende el objeto <xref:Microsoft.Office.Interop.Excel.Range> proporcionando los tipos <xref:Microsoft.Office.Tools.Excel.NamedRange> y <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Estos tipos tienen la mayoría de las características de un objeto <xref:Microsoft.Office.Interop.Excel.Range>, además de nuevas características como la capacidad de enlace de datos y nuevos eventos. Para obtener más información, vea [NamedRange control](../vsto/namedrange-control.md) y [XmlMappedRange (control](../vsto/xmlmappedrange-control.md).

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a> Usar la documentación del modelo de objetos de Excel
 Para obtener información completa sobre el modelo de objetos de Excel, puede consultar la referencia del ensamblado de interoperabilidad primario (PIA) de Excel y la referencia del modelo de objetos VBA.

### <a name="primary-interop-assembly-reference"></a>Referencia de ensamblado de interoperabilidad primario
 La documentación de referencia de los PIA de Excel describe los tipos Del ensamblado de interoperabilidad primario para Excel. Esta documentación está disponible en la siguiente ubicación: [referencia de ensamblado de interoperabilidad primario de Excel 2010](office-primary-interop-assemblies.md).

 Para obtener más información sobre el diseño del PIA de Excel, como las diferencias entre las clases y las interfaces en el PIA y cómo se implementan los eventos en el PIA, consulte [información general de las clases e interfaces de los ensamblados de interoperabilidad primarios de Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Referencia del modelo de objetos de VBA
 La referencia del modelo de objetos de VBA documenta el modelo de objetos de Excel tal como se expone al código de Visual Basic para Aplicaciones (VBA). Para obtener más información, vea [Referencia del modelo de objetos de Excel 2010](/office/vba/api/overview/Excel/object-model).

 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del PIA de Excel. Por ejemplo, el objeto de hoja de cálculo de la referencia del modelo de objetos VBA corresponde al <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto del Pia de Excel. Aunque la referencia del modelo de objetos VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe traducir el código VBA de esta referencia a Visual Basic o Visual C# si quiere usarlo en un proyecto de Excel creado con Visual Studio.

### <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Soluciones de Excel](../vsto/excel-solutions.md)|Explica cómo crear personalizaciones de nivel de documento y complementos de VSTO para Microsoft Office Excel.|
|[Trabajar con rangos](../vsto/working-with-ranges.md)|Proporciona ejemplos que muestran cómo realizar tareas habituales con rangos.|
|[Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)|Proporciona ejemplos que muestran cómo realizar tareas habituales con hojas de cálculo.|
|[Trabajar con libros](../vsto/working-with-workbooks.md)|Proporciona ejemplos que muestran cómo realizar tareas habituales con libros.|
