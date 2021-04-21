---
title: 'Cómo: Rellenar controles ListObject con datos'
description: Use el enlace de datos para agregar rápidamente datos al documento. También puede desconectar el objeto de lista para que muestre los datos, pero ya no esté enlazado al origen de datos.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 91fb4da23f388234e3800805e2beb3b7a8fbb20e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828922"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Cómo: Rellenar controles ListObject con datos
  Puede utilizar el enlace de datos como una manera de agregar datos rápidamente al documento. Después de enlazar datos a un objeto de lista, puede desconectar el objeto de lista para que muestre los datos, pero ya no esté enlazado al origen de datos.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

### <a name="to-bind-data-to-a-listobject-control"></a>Para enlazar datos a un control ListObject

1. Cree un elemento <xref:System.Data.DataTable> en el nivel de clase.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet20":::

2. Agregue datos y columnas de ejemplo en el controlador de eventos `Startup` de la clase `Sheet1` (en un proyecto de nivel de documento) o una clase `ThisAddIn` (en un proyecto de nivel de aplicación).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet21":::

3. Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. El orden de las columnas en el objeto de lista puede diferir del orden en que aparecen en el elemento <xref:System.Data.DataTable>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet22":::

### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Para desconectar el control ListObject del origen de datos

1. Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> de `List1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet23":::

## <a name="compile-the-code"></a>Compilar el código
 En este ejemplo de código se supone que dispone de un elemento <xref:Microsoft.Office.Tools.Excel.ListObject> existente denominado `list1` en la hoja de cálculo en la que aparece este código.

## <a name="see-also"></a>Consulte también
- [Extensión de documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Asignación de columnas ListObject a datos](../vsto/how-to-map-listobject-columns-to-data.md)
- [Automatización de Excel mediante objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Control ListObject](../vsto/listobject-control.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Cómo: Rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)
