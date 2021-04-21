---
title: 'Cómo: Asignar columnas ListObject a datos'
description: Obtenga información sobre cómo puede asignar las columnas que desea que aparezcan en listObject al llamar al método SetDataBinding.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68cb12503d0f8ad59de92f965c0ed51fbc0d7f40
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827466"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Cómo: Asignar columnas ListObject a datos
  Al enlazar un control <xref:Microsoft.Office.Tools.Excel.ListObject> a un <xref:System.Data.DataTable>, puede que no desee mostrar todas las columnas de una lista o puede que tenga algunas columnas que no están enlazadas a datos. Puede asignar las columnas que desea que aparezca en <xref:Microsoft.Office.Tools.Excel.ListObject> al llamar al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Asignar columnas

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Para asignar una tabla de datos a columnas en una lista

1. Cree la <xref:System.Data.DataTable> en el nivel de clase.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet16":::

2. Agregue columnas y datos de ejemplo en el controlador de eventos de la clase (en un proyecto de nivel de documento) o de la clase (en un proyecto `Startup` `Sheet1` de complemento de `ThisAddIn` VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet17":::

3. Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. El objeto de lista se enlazará al recién creado, pero el orden de las columnas del objeto de lista será diferente del orden en que <xref:System.Data.DataTable> aparecen en <xref:System.Data.DataTable> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet18":::

## <a name="specify-unmapped-columns"></a>Especificación de columnas no seleccionadas
 Al asignar columnas a un <xref:System.Data.DataTable>, también puede especificar que algunas columnas no se enlacen a datos pasando una cadena vacía. A continuación, se agrega al control <xref:Microsoft.Office.Tools.Excel.ListObject> una nueva columna que no esté enlazada a datos.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Para especificar una columna no asignada al asignar columnas ListObject

1. Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. Use una cadena vacía para indicar dónde se agrega una columna no asignada; en este caso, entre la columna de título y la última columna de nombre.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet19":::

## <a name="compile-the-code"></a>Compilar el código
 En este ejemplo de código se supone que dispone de un elemento <xref:Microsoft.Office.Tools.Excel.ListObject> existente denominado `list1` en la hoja de cálculo en la que aparece este código.

## <a name="see-also"></a>Consulte también
- [Extensión de documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cómo: Rellenar controles ListObject con datos](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatización de Excel mediante objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Control ListObject](../vsto/listobject-control.md)
