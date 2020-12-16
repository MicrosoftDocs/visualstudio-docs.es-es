---
title: Elemento host del libro
description: Obtenga información sobre que el elemento host del libro es un tipo que extiende el tipo de libro desde el ensamblado de interoperabilidad primario de Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d3d5b7efadefd77be7ce25026c8f485ee0ef133
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528347"
---
# <a name="workbook-host-item"></a>Elemento host del libro
  El elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> es un tipo que extiende el tipo <xref:Microsoft.Office.Interop.Excel.Workbook> del ensamblado de interoperabilidad primario de Excel. El elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> proporciona todas las mismas propiedades, los mismos métodos y eventos que un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> , pero también ofrece características adicionales.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En proyectos de nivel de documento, existe un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> predeterminado que representa el libro del proyecto. En los proyectos de complemento de VSTO, puede generar elementos host <xref:Microsoft.Office.Tools.Excel.Workbook> en tiempo de ejecución.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Descripción del elemento host de libro en los proyectos de nivel de documento
 Para acceder al documento del proyecto, utilice la clase `ThisWorkbook` . La clase `ThisWorkbook` le da acceso a los miembros del elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> para que pueda realizar tareas básicas durante la personalización, como por ejemplo, ejecutar el código cuando se abra o se cierre el libro. Para obtener más información, consulte [Personalización de nivel de documento de programa](../vsto/programming-document-level-customizations.md).

 La clase `ThisWorkbook` proporciona una ubicación en la que puede empezar a escribir el código del proyecto. Como esta clase proporciona las mismas propiedades, métodos y eventos que el objeto <xref:Microsoft.Office.Interop.Excel.Workbook> que se encuentra en el ensamblado de interoperabilidad primario de Excel, también puede usar `ThisWorkbook` para obtener acceso al modelo de objetos de Excel. Para obtener más información, vea [información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).

 Haga doble clic en el elemento de proyecto **ThisWorkbook** en el **Explorador de soluciones** para mostrar el diseñador del libro y ver las propiedades y los eventos del libro en la ventana **Propiedades** .

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Limitaciones del elemento host de libro en los proyectos de nivel de documento
 Un proyecto de nivel de documento puede contener solamente un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> (es decir, la clase `ThisWorkbook` ). No puede agregar nuevos elementos host <xref:Microsoft.Office.Tools.Excel.Workbook> al proyecto en tiempo de diseño, ni tampoco crear nuevos elementos host <xref:Microsoft.Office.Tools.Excel.Workbook> en tiempo de ejecución desde una personalización de nivel de documento.

 Si crea un nuevo libro de Excel en tiempo de ejecución, será del tipo <xref:Microsoft.Office.Interop.Excel.Workbook>. Como no se trata de un elemento host, este no puede contener controles host ni controles de Windows Forms. Para obtener más información sobre la creación de libros en tiempo de ejecución, vea [Cómo: crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md).

 El elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> no actúa como un contenedor para los controles host. Por lo tanto, no es posible agregar ningún control visible al libro, pero puede agregar componentes, como un elemento <xref:System.Data.DataSet>, de modo que los componentes puedan compartirse en todas las hojas de cálculo. En un proyecto de nivel de documento, los componentes disponibles para el libro se pueden encontrar en la pestaña **Componentes** , en la pestaña **Datos** y la pestaña **Todos los formularios Windows Forms** del **Cuadro de herramientas**.

> [!NOTE]
> Las herramientas de desarrollo de Office en Visual Studio no admiten libros compartidos.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Descripción de los elementos host de libro en proyectos de complemento de VSTO
 En los proyectos de complemento de VSTO, puede generar un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> en tiempo de ejecución para cualquier libro que esté abierto en Excel. Para generar un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook>, use el método `GetVstoObject`. Para obtener más información, vea [ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Consulte también
- [Ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Elemento host de hoja de cálculo](../vsto/worksheet-host-item.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
