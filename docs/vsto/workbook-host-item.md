---
title: Elemento host Workbook
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
ms.openlocfilehash: b8ffe18ea3407480faa69a6b9b3ba4309b28b279
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625271"
---
# <a name="workbook-host-item"></a>Elemento host Workbook
  El elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> es un tipo que extiende el tipo <xref:Microsoft.Office.Interop.Excel.Workbook> del ensamblado de interoperabilidad primario de Excel. El elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> proporciona todas las mismas propiedades, los mismos métodos y eventos que un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> , pero también ofrece características adicionales.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En proyectos de nivel de documento, existe un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> predeterminado que representa el libro del proyecto. En proyectos de complemento VSTO, puede generar <xref:Microsoft.Office.Tools.Excel.Workbook> hospedar elementos en tiempo de ejecución.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Comprender el elemento host workbook en los proyectos de nivel de documento
 Para acceder al documento del proyecto, utilice la clase `ThisWorkbook` . La clase `ThisWorkbook` le da acceso a los miembros del elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> para que pueda realizar tareas básicas durante la personalización, como por ejemplo, ejecutar el código cuando se abra o se cierre el libro. Para obtener más información, consulte [programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).

 La clase `ThisWorkbook` proporciona una ubicación en la que puede empezar a escribir el código del proyecto. Como esta clase proporciona las mismas propiedades, métodos y eventos que el objeto <xref:Microsoft.Office.Interop.Excel.Workbook> que se encuentra en el ensamblado de interoperabilidad primario de Excel, también puede usar `ThisWorkbook` para obtener acceso al modelo de objetos de Excel. Para obtener más información, consulte [información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).

 Haga doble clic en el elemento de proyecto **ThisWorkbook** en el **Explorador de soluciones** para mostrar el diseñador del libro y ver las propiedades y los eventos del libro en la ventana **Propiedades** .

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Limitaciones del elemento de host de libro en proyectos de nivel de documento
 Un proyecto de nivel de documento puede contener solamente un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> (es decir, la clase `ThisWorkbook` ). No puede agregar nuevos <xref:Microsoft.Office.Tools.Excel.Workbook> elementos host para el proyecto en tiempo de diseño, y que no se puede crear nuevos <xref:Microsoft.Office.Tools.Excel.Workbook> elementos en tiempo de ejecución desde una personalización de nivel de documento host.

 Si crea un nuevo libro de Excel en tiempo de ejecución, será del tipo <xref:Microsoft.Office.Interop.Excel.Workbook>. Como no se trata de un elemento host, este no puede contener controles host ni controles de Windows Forms. Para obtener más información sobre la creación de los libros en tiempo de ejecución, vea [Cómo: Crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md).

 El elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> no actúa como un contenedor para los controles host. Por lo tanto, no es posible agregar ningún control visible al libro, pero puede agregar componentes, como un elemento <xref:System.Data.DataSet>, de modo que los componentes puedan compartirse en todas las hojas de cálculo. En un proyecto de nivel de documento, los componentes disponibles para el libro se pueden encontrar en la pestaña **Componentes** , en la pestaña **Datos** y la pestaña **Todos los formularios Windows Forms** del **Cuadro de herramientas**.

> [!NOTE]
>  Las herramientas de desarrollo de Office en Visual Studio no admiten libros compartidos.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Comprender los elementos host de libro en proyectos de complemento VSTO
 En proyectos de complemento VSTO, puede generar un <xref:Microsoft.Office.Tools.Excel.Workbook> elemento host en tiempo de ejecución para cualquier libro que está abierto en Excel. Para generar un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook>, use el método `GetVstoObject`. Para obtener más información, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Vea también
- [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)
- [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Elemento host Worksheet](../vsto/worksheet-host-item.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
