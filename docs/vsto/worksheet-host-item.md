---
title: Elemento Host Worksheet | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c89fa79a73393afa2919554de790c307b2ea68b5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="worksheet-host-item"></a>Elemento host Worksheet
  El elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> es un tipo que extiende el tipo <xref:Microsoft.Office.Interop.Excel.Worksheet> del ensamblado de interoperabilidad primario de Excel. Asimismo, el elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> ofrece las mismas propiedades, los mismos métodos y eventos que un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> , pero también expone eventos adicionales y sirve de contenedor para los controles host y para los controles de Windows Forms.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En los proyectos de nivel de documento, puede agregar elementos host <xref:Microsoft.Office.Tools.Excel.Worksheet> al proyecto en tiempo de diseño. En los proyectos de complemento de VSTO, puede generar elementos host <xref:Microsoft.Office.Tools.Excel.Worksheet> en tiempo de ejecución.  
  
## <a name="understanding-worksheet-host-items-in-document-level-projects"></a>Descripción de los elementos host de hojas de cálculo en proyectos de nivel del documento  
 Cuando se crea un proyecto de nivel de documento para Excel, Visual Studio crea automáticamente tres elementos host <xref:Microsoft.Office.Tools.Excel.Worksheet> en el proyecto. Los nombres predeterminados de las hojas de cálculo son `Sheet1`, `Sheet2`y `Sheet3`. Si crea un proyecto basado en un libro existente, el número de elementos host depende del número de hojas de cálculo del libro.  
  
 Estas clases de hojas de cálculo ofrecen acceso a los miembros del elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> para realizar tareas básicas en la personalización, como modificar el contenido de una hoja de cálculo. También puede utilizar estas clases para agregar controles a hojas de cálculo. Si combina diferentes conjuntos de controles y escribe el código, puede enlazar los controles a los datos, recopilar información del usuario y responder a las acciones del usuario. Para obtener más información, consulta [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 Las clases de hojas de cálculo ofrecen una ubicación en la que puede empezar a escribir código en el proyecto. Como esta clase proporciona las mismas propiedades, métodos y eventos que el objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> que se encuentra en el ensamblado de interoperabilidad primario de Excel, también puede usar estas clases para obtener acceso al modelo de objetos de Excel. Para obtener más información, consulta [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
 En los proyectos de nivel de documento, puede agregar más elementos host <xref:Microsoft.Office.Tools.Excel.Worksheet> al proyecto en tiempo de diseño si agrega una nueva hoja de cálculo al libro en el diseñador.  
  
### <a name="renaming-worksheets"></a>Cambiar el nombre de las hojas de cálculo  
 En un proyecto de nivel de documento, puede cambiar el nombre de las hojas de cálculo en el diseñador de Visual Studio, pero esto solo cambia el nombre para mostrar de la hoja de cálculo. El nombre de programación sigue siendo el nombre predeterminado de la hoja de cálculo. Si cambia el nombre de la hoja de cálculo en la ventana **Propiedades** , solo cambia el nombre de programación.  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Limitaciones del elemento host de hoja de cálculo en los proyectos de nivel de documento  
 No es posible crear nuevos elementos host <xref:Microsoft.Office.Tools.Excel.Worksheet> en tiempo de ejecución en un proyecto de nivel de documento. Si crea una nueva hoja de cálculo de Excel en tiempo de ejecución, será del tipo <xref:Microsoft.Office.Interop.Excel.Worksheet>. Como no se trata de un elemento host, este no puede contener controles host ni controles de Windows Forms. Para obtener más información acerca de cómo crear documentos en tiempo de ejecución, consulte [Cómo: mediante programación agregar nuevas hojas de cálculo a libros](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## <a name="understanding-worksheet-host-items-in-vsto-add-in-projects"></a>Descripción de los elementos host de hoja de cálculo en proyectos de complemento de VSTO  
 En los proyectos de nivel de aplicación, puede generar un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> en tiempo de ejecución para cualquier hoja de cálculo que esté abierta en Excel. Puede usar el elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> para agregar controles a la hoja de cálculo asociada o para administrar los eventos que no estén disponibles en los objetos <xref:Microsoft.Office.Interop.Excel.Worksheet> .  
  
 Para generar un <xref:Microsoft.Office.Tools.Excel.Worksheet> elemento host, utilice el método GetVstoObject. Para obtener más información, consulta [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento Host Workbook](../vsto/workbook-host-item.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  