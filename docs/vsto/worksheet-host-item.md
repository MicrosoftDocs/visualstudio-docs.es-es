---
title: Elemento host Worksheet
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
ms.openlocfilehash: 4052e7d9b096d9bae6671834369ece6d31bee4a0
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258923"
---
# <a name="worksheet-host-item"></a>Elemento host Worksheet
  El elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> es un tipo que extiende el tipo <xref:Microsoft.Office.Interop.Excel.Worksheet> del ensamblado de interoperabilidad primario de Excel. Asimismo, el elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> ofrece las mismas propiedades, los mismos métodos y eventos que un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> , pero también expone eventos adicionales y sirve de contenedor para los controles host y para los controles de Windows Forms.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En los proyectos de nivel de documento, puede agregar elementos host <xref:Microsoft.Office.Tools.Excel.Worksheet> al proyecto en tiempo de diseño. En proyectos de complemento VSTO, puede generar <xref:Microsoft.Office.Tools.Excel.Worksheet> hospedar elementos en tiempo de ejecución.  
  
## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Comprender los elementos host de hoja de cálculo en proyectos de nivel de documento  
 Cuando se crea un proyecto de nivel de documento para Excel, Visual Studio crea automáticamente tres elementos host <xref:Microsoft.Office.Tools.Excel.Worksheet> en el proyecto. Los nombres predeterminados de las hojas de cálculo son `Sheet1`, `Sheet2`y `Sheet3`. Si crea un proyecto basado en un libro existente, el número de elementos host depende del número de hojas de cálculo del libro.  
  
 Estas clases de hojas de cálculo ofrecen acceso a los miembros del elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> para realizar tareas básicas en la personalización, como modificar el contenido de una hoja de cálculo. También puede utilizar estas clases para agregar controles a hojas de cálculo. Si combina diferentes conjuntos de controles y escribe el código, puede enlazar los controles a los datos, recopilar información del usuario y responder a las acciones del usuario. Para obtener más información, consulte [programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
 Las clases de hojas de cálculo ofrecen una ubicación en la que puede empezar a escribir código en el proyecto. Como esta clase proporciona las mismas propiedades, métodos y eventos que el objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> que se encuentra en el ensamblado de interoperabilidad primario de Excel, también puede usar estas clases para obtener acceso al modelo de objetos de Excel. Para obtener más información, consulte [información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).  
  
 En los proyectos de nivel de documento, puede agregar más elementos host <xref:Microsoft.Office.Tools.Excel.Worksheet> al proyecto en tiempo de diseño si agrega una nueva hoja de cálculo al libro en el diseñador.  
  
### <a name="rename-worksheets"></a>Cambiar el nombre de las hojas de cálculo  
 En un proyecto de nivel de documento, puede cambiar el nombre de las hojas de cálculo en el diseñador de Visual Studio, pero esto solo cambia el nombre para mostrar de la hoja de cálculo. El nombre de programación sigue siendo el nombre predeterminado de la hoja de cálculo. Si cambia el nombre de la hoja de cálculo en la ventana **Propiedades** , solo cambia el nombre de programación.  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Limitaciones del elemento de host de hoja de cálculo en proyectos de nivel de documento  
 No se puede crear de nuevo <xref:Microsoft.Office.Tools.Excel.Worksheet> elementos en tiempo de ejecución en un proyecto de nivel de documento host. Si crea una nueva hoja de cálculo de Excel en tiempo de ejecución, será del tipo <xref:Microsoft.Office.Interop.Excel.Worksheet>. Como no se trata de un elemento host, este no puede contener controles host ni controles de Windows Forms. Para obtener más información sobre la creación de documentos en tiempo de ejecución, consulte [Cómo: agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Comprender los elementos host de hoja de cálculo en proyectos de complemento VSTO  
 En los proyectos de nivel de aplicación, puede generar un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> en tiempo de ejecución para cualquier hoja de cálculo que esté abierta en Excel. Puede usar el elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> para agregar controles a la hoja de cálculo asociada o para administrar los eventos que no estén disponibles en los objetos <xref:Microsoft.Office.Interop.Excel.Worksheet> .  
  
 Para generar un <xref:Microsoft.Office.Tools.Excel.Worksheet> elemento host, utilice el `GetVstoObject` método. Para obtener más información, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  