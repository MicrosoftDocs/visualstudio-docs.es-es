---
title: Limitaciones de programación de elementos y controles host
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 098145ca901b1f16974058513d3781fc4621f217
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584482"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Limitaciones de programación de elementos y controles host
  Los elementos y controles host están diseñados para comportarse como los objetos de Microsoft Office Word o Microsoft Office Excel nativos correspondientes, pero con funcionalidad adicional. Sin embargo, hay algunas diferencias fundamentales entre el comportamiento de los elementos y los controles host y los objetos nativos de Office en tiempo de ejecución.

 Para obtener información general sobre los elementos host y los controles host, vea [información general sobre elementos y controles](../vsto/host-items-and-host-controls-overview.md)host.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Crear elementos host mediante programación
 Cuando se crea o se abre mediante programación un documento, un libro o una hoja de cálculo en tiempo de ejecución usando el modelo de objetos de Word o Excel, el elemento no es un elemento host, sino que el nuevo objeto es un objeto de Office nativo. Por ejemplo, si usa el método <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> para crear un nuevo documento de Word en tiempo de ejecución, será un objeto <xref:Microsoft.Office.Interop.Word.Document> nativo en lugar de un elemento host <xref:Microsoft.Office.Tools.Word.Document> . De forma similar, cuando crea una nueva hoja de cálculo en tiempo de ejecución mediante el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> , obtiene un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo en lugar de un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> .

 En los proyectos de nivel de documento, no es posible crear elementos host en tiempo de ejecución. Los elementos host pueden crearse solo en tiempo de diseño en proyectos de nivel de documento. Para obtener más información, vea elemento [host de documento](../vsto/document-host-item.md), elemento host de [libro](../vsto/workbook-host-item.md)y [elemento host de hoja de cálculo](../vsto/worksheet-host-item.md).

 En los proyectos de complemento de VSTO, se puede crear los elementos host <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>o <xref:Microsoft.Office.Tools.Excel.Worksheet> en tiempo de ejecución. Para obtener más información, vea [ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="programmatically-create-host-controls"></a>Crear controles host mediante programación
 Puede agregar mediante programación controles host a un elemento host <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet> en tiempo de ejecución. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

 No se pueden agregar controles host a <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet>nativo.

> [!NOTE]
> Los controles host siguientes no se pueden agregar mediante programación a hojas de cálculo ni documentos: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>y <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Descripción de las diferencias de tipos entre elementos host, controles host y objetos de Office nativos
 Existe un objeto nativo subyacente de Microsoft Office Word o Microsoft Office Excel por cada elemento y control host. Puede tener acceso al objeto subyacente mediante la propiedad InnerObject del elemento host o el control host. Sin embargo, no hay forma de convertir un objeto nativo de Office en el elemento o control host correspondiente. Si se intenta convertir un objeto nativo de Office en el tipo de un elemento o control host, se produce una <xref:System.InvalidCastException> .

 Hay varios escenarios donde las diferencias entre los tipos de elementos y controles host y los objetos nativos de Office subyacentes pueden afectar al código.

### <a name="pass-host-controls-to-methods-and-properties"></a>Pasar controles host a métodos y propiedades
 En Word, no se puede pasar un control host a un método o una propiedad que requiera un objeto nativo de Word como parámetro. Debe utilizar la propiedad InnerObject del control host para devolver el objeto de Word nativo subyacente. Por ejemplo, puede pasar un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> a un método pasando la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> del control host <xref:Microsoft.Office.Tools.Word.Bookmark> al método.

 En Excel, debe usar la propiedad InnerObject del control host para pasar el control host a un método o propiedad cuando el método o la propiedad esperan el objeto de Excel subyacente.

 En el ejemplo siguiente se crea un control <xref:Microsoft.Office.Tools.Excel.NamedRange> para pasarlo al método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> . El código usa la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> del rango con nombre para devolver el <xref:Microsoft.Office.Interop.Excel.Range> subyacente de Office necesario para el método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> .

 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]

### <a name="return-types-of-native-office-methods-and-properties"></a>Tipos de valor devueltos de propiedades y métodos nativos de Office
 La mayoría de los métodos y propiedades de lo elementos host devuelven el objeto de Office nativo subyacente en el que se basa el elemento host. Por ejemplo, la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> de un control host <xref:Microsoft.Office.Tools.Excel.NamedRange> en Excel devuelve un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> en lugar de un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> . De igual forma, la propiedad <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> de un control host <xref:Microsoft.Office.Tools.Word.RichTextContentControl> en Word devuelve un objeto <xref:Microsoft.Office.Interop.Word.Document> en lugar de un elemento host <xref:Microsoft.Office.Tools.Word.Document> .

### <a name="access-collections-of-host-controls"></a>Acceder a colecciones de controles host
 El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] no proporciona colecciones individuales para cada tipo de control host. En su lugar, use la propiedad Controls de un elemento host para recorrer en iteración todos los controles administrados (tanto controles host como controles Windows Forms) en el documento o la hoja de cálculo y, a continuación, buscar los elementos que coinciden con el tipo de control host que le interesa. En el siguiente ejemplo de código se examina cada control en un documento de Word y se determina si el control es un control <xref:Microsoft.Office.Tools.Word.Bookmark>.

 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]

 Para obtener más información sobre la propiedad controles de los elementos host, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Los modelos de objetos de Word y Excel incluyen propiedades que exponen colecciones de controles nativos en los documentos y las hojas de cálculo. No se puede acceder a los controles administrados mediante estas propiedades. Por ejemplo, no es posible enumerar cada control host <xref:Microsoft.Office.Tools.Word.Bookmark> en un documento mediante la propiedad <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Document> o la propiedad <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> de un objeto <xref:Microsoft.Office.Tools.Word.Document>. Estas propiedades incluyen solo los controles <xref:Microsoft.Office.Interop.Word.Bookmark> del documento; no contienen los controles host <xref:Microsoft.Office.Tools.Word.Bookmark> del documento.

## <a name="see-also"></a>Vea también
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Elemento host de hoja de cálculo](../vsto/worksheet-host-item.md)
- [Elemento host del libro](../vsto/workbook-host-item.md)
- [Elemento host de documento](../vsto/document-host-item.md)
